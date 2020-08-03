## Cotizaciones de los equipos

Por supuesto, no podemos cubrir cada cambio que ha sucedido. Entonces nos comunicamos y preguntamos a algunos de nuestros equipos de qué cambios están más orgullosos:

> Para rustdoc, las grandes cosas fueron:
> - La documentación generada automáticamente para implementaciones generales
> - La búsqueda en sí y sus optimizaciones (la última es convertirla en JSON)
> - La posibilidad de probar con mayor precisión los bloques de código de documento "compile_fail, should_panic, allow_fail"
> - Las pruebas de documentos ahora se generan como sus propios binarios separados.
> - Guillaume Gómez ([rustdoc])

> ¡Rust ahora tiene soporte básico de IDE! Entre IntelliJ Rust, RLS y el analizador de óxido, creo que la mayoría de los usuarios deberían poder encontrar una experiencia "no horrible" para el editor de su elección. Hace cinco años, "escribir Rust" significaba usar la configuración de Vim / Emacs de la vieja escuela.
> - Aleksey Kladov ([IDEs y editores] [ides])

> Para mí eso sería: Agregar soporte de primera clase para arquitecturas integradas populares y lograr un ecosistema esforzado para hacer que el desarrollo de microcontroladores con Rust sea una experiencia fácil y segura, pero divertida.
> - Daniel Egger ([GT integrado] [ewg])

> El equipo de lanzamiento solo ha existido desde (aproximadamente) principios de 2018, pero incluso en ese momento, hemos logrado ~ 40000 confirmaciones solo en rust-lang / rust sin ninguna regresión significativa en estable.
> Considerando lo rápido que estamos mejorando el compilador y las bibliotecas estándar, creo que es realmente impresionante (aunque, por supuesto, el equipo de lanzamiento no es el único contribuyente aquí). En general, he descubierto que el equipo de lanzamiento ha hecho un excelente trabajo al escalar para aumentar el tráfico en rastreadores de problemas, relaciones públicas que se archivan, etc.
> - Mark Rousskov ([Lanzamiento] [lanzamiento])

> En los últimos 3 años, logramos convertir a [Miri] de intérprete experimental en una herramienta práctica para explorar el diseño del lenguaje y encontrar errores en el código real, una gran combinación de teoría y práctica de PL. En el lado teórico tenemos [Stacked Borrows] , la propuesta más concreta para un modelo de alias Rust hasta ahora. Desde el punto de vista práctico, aunque inicialmente solo revisamos algunas bibliotecas clave en Miri, recientemente vimos una gran aceptación de personas que utilizan Miri para [encontrar y corregir errores](https://github.com/rust-lang/miri/#bugs-found-by-miri) en sus propias cajas y dependencias, y una aceptación similar en los contribuyentes que mejoraron Miri, por ejemplo. agregando soporte para acceso al sistema de archivos, desenrollado y concurrencia.
> - Ralf Jung ([Miri])

> Si tuviera que elegir una cosa de la que estoy más orgulloso, fue el trabajo en vidas no léxicas (NLL). No solo porque creo que marcó una gran diferencia en la usabilidad de Rust, sino también por la forma en que lo implementamos al formar el grupo de trabajo NLL. Este grupo de trabajo atrajo a muchos colaboradores excelentes, muchos de los cuales todavía están trabajando en el compilador hoy. ¡Código abierto en su máxima expresión!
> - Niko Matsakis ([Idioma])


[Miri]: https://github.com/rust-lang/miri
[Stacked Borrows]: https://github.com/rust-lang/unsafe-code-guidelines/blob/master/wip/stacked-borrows.md