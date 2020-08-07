# Apéndice A: Cree una caja de arena protegida de OJS 3 preparada con Git

El siguiente documento describe un flujo de trabajo general para crear un sandbox basado en git de un diario de producción que actualmente no está en git. Proporciona instrucciones sobre cómo limitar el acceso accidental, el correo electrónico saliente, etc. YMMV. Adáptese a su propio entorno; Úselo bajo su propio riesgo.

## Preparar el entorno de Git

El archivo README aquí: [https://github.com/pkp/ojs](https://github.com/pkp/ojs) tiene instrucciones sobre cómo instalar desde git. Lo que hacemos es lo siguiente:

1. Cree un usuario y una base de datos MySQL OJS. El comando que usamos es el siguiente; puede ser diferente para usted dependiendo de su entorno, acceso a root, etc .:

    ```
    mysql -u root -e "CREATE DATABASE `ojs-sandbox` DEFAULT CHARACTER SET UTF8; GRANT ALL ON `ojs-sandbox`.* TO `ojs`@localhost IDENTIFIED BY 'ojs'" -p
    ```

2. Consulte la rama estable de GitHub. La ruta será específica para su instalación de Apache, y puede actualizar la rama a la última rama estable:

    ```
    cd <httpd-docs-folder>
    git clone -n https://github.com/pkp/ojs.git ./
    git checkout -b ojs-3_1_0 --no-track origin/ojs-stable-3_1_0
    cp config.TEMPLATE.inc.php config.inc.php
    chmod -R 755 *
    chmod 600 config.inc.php
    ```

3. Obtenga la biblioteca PKP correspondiente y la rama estable de pago de GitHub, asegurándose de que la rama corresponda a la misma rama mencionada anteriormente:

    ```
    git submodule update --init --recursive
    cd lib/pkp
    git checkout -b ojs-3_1_0 --no-track origin/ojs-stable-3_1_0
    ```

4. Instalar compositor:

    ```
    cd ../..
    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
    php -r "if (hash_file('sha384', 'composer-setup.php') === 'e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
    php composer-setup.php
    php -r "unlink('composer-setup.php');"
    ```

5. Instale las dependencias del compositor:

    ```
    cd lib/pkp
    php ../../composer.phar --no-dev install
    cd ../../plugins/paymethod/paypal
    php ../../../composer.phar --no-dev install
    cd ../../../plugins/generic/citationStyleLanguage
    php ../../../composer.phar --no-dev install
    ```

6. Instale las dependencias de Node.js (NOTA: npm debe estar instalado en el servidor):

    ```
    cd ../../..
    npm install
    npm run build
    ```

7. Crea un nuevo archivo de configuración:

    ```
    cd ../../..
    cp config.TEMPLATE.inc.php config.inc.php
    ```

En este punto, debería tener un sistema OJS 3 y una base de datos completamente preparados y listos para funcionar.

## **Elimina cualquier posibilidad de que las tareas programadas se activen en el servidor de ensayo**

Elimine el complemento Acron (el complemento Acron puede activar tareas programadas para que se ejecuten sin depender de un trabajo cron):

```
rm -rf plugins/generic/acron
rm -rf lib/pkp/plugins/generic/acron
```

Este complemento tendrá que reinstalarse después de pasar a producción, lo cual, si está ejecutando cosas a través de git, puede hacerlo de la siguiente manera:

```
git checkout plugins/generic/acron
cd lib/pkp
git checkout plugins/generic/acron
```

## Realice una copia de seguridad y copie los archivos de envío, públicos y de base de datos

Estos comandos se realizan en la instalación de producción y son sus comandos típicos de respaldo / archivo.

Base de datos: usualmente usamos mysqldump para hacer una copia de la base de datos:

```
mysqldump db\_name --opt --default-character-set=utf8 --result-file=~/client\_db.sql -u db\_user -p
```

Archivos de envío: puede encontrar el directorio correcto en el archivo config.inc.php de OJS, busque el parámetro "files_dir". Normalmente comprimimos esto para que sea más fácil de transferir:

```
cd <submission files dir>
tar -cvzf ~/files.tar.gz ./
```

Archivos públicos: esto puede incluir cosas como imágenes de portada, etc., y se encuentra en el directorio del sistema OJS, en el subdirectorio "público /":

```
cd <ojs-system-dir>/public
tar -cvzf ~/public.tar.gz ./
```

Transfiera los archivos al servidor de ensayo: generalmente usamos `scp` o `rsync` . La gente de su sistema debería saber qué usar aquí, pero para nosotros suele ser algo como:

```
rsync -avz client\_db.sql username@stagingserver.org:/~
rsync -avz public.tar.gz username@stagingserver.org:/~
rsync -avz files.tar.gz username@stagingserver.org:/~
```

## Instale los archivos de envío, públicos y de base de datos en las ubicaciones correctas

Instale la base de datos (esto puede variar según el nombre de usuario, el nombre de la base de datos y la contraseña que especificó anteriormente):

```
mysql -u ojs-sandbox -p ojs-sandbox < ~/client\_db.sql
```

Instale los archivos de envío:

```
tar -xvf ~/files.tar.gz <files directory>
```

Instale los archivos públicos:

```
tar xvf ~/public.tar.gz <ojs-folder>/public/
```

Edite el archivo `config.inc.php` y cambie los parámetros de la base de datos y files_dir.

```
vi config.inc.php
```

En este punto, todos los archivos y tablas de base de datos relevantes deben estar en su lugar, y el archivo de configuración debe apuntar a esas ubicaciones.

## Desinfecte todos los correos electrónicos del sistema para que el sistema no envíe correos electrónicos por accidente.

Si está ejecutando la caja de arena en su propio servidor, es posible que desee considerar la posibilidad de deshabilitar todas y cada una de las funciones de correo electrónico en el servidor. Pero lo siguiente también funcionará (ya que cualquier correo electrónico que se envíe se enviará a direcciones de correo electrónico que no sean de producción).

You can set your email addresses to a [Mailinator](https://www.mailinator.com/) address, which will mean the emails will be sent to an accessible public inbox (e.g. username@mailinator.com), or use a fake email address. You can also set emails based on specific user roles. You will first need to access your database:

```
mysql -u ojs-sandbox -p ojs-sandbox
```

Para configurar todas las direcciones de correo electrónico de los usuarios en username@mailinator.com:

```
UPDATE users SET email=CONCAT\(username,'@mailinator.com’\);
```

Para configurar todos los correos electrónicos relacionados con el envío, por ejemplo, los de los contribuyentes, en test@example.com:

```
UPDATE authors SET email = 'test@example.com’
```

## (Opcional) Agregue protección con contraseña al sitio para que no se acceda accidentalmente, no se rastree, etc.

Hacemos esto para todos los sandboxes agregando protección .htaccess y .htpasswd a la raíz web del sandbox. La gente de su sistema sabría cómo hacer esto.

## Ejecute la actualización

Desde la raíz web de la zona de pruebas, ejecute este comando:

```
php tools/upgrade.php upgrade
```

En este punto, si se completa la actualización, debería tener una actualización de sandbox limpia y protegida que ejecute OJS 3 que puede administrar a través de git.
