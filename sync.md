---
layout: post
title: All Markdown formats
---

# Basics

It's very easy to make some words **bold** __bold__ and other words *italic* _italic_ with Markdown. _You **can** combine them_. And ***triple*** or ___triple___. You can even [link to Google!](http://google.com) and also [link with title](http://google.com "title")
Text line break and ~~strikethrough~~

You can use one `#` all the way up to `######` six for different heading sizes. <a href="http://google.com" target="_blank">Test link</a>

If you'd like to quote someone, use the > character before the line:

> Coffee. The finest organic suspension ever devised... I beat the Borg with it.
> - Captain Janeway
>   - elem

# This is an `<h1>` tag

This is also an `<h1>`
=============

## This is an `<h2>` tag

This is also an `<h2>`
-------------

###### This is an `<h6>` tag

## Lists

Sometimes you want numbered lists:

1. One
2. Two

*  Red
*  Green

+  Red
+  Green

- Dashes work just as well
- And if you have sub points, put two spaces before the dash or star:
  - Like this
  - And this
    - Also this
    - And this

# Horizontal rules

* * *

***

*****

- - -

---------------------------------------

# Images

![External image](https://octodex.github.com/images/yaktocat.png)

![Internal image](/img/screwdriver.png "Optional title")

# Codes

There are many different ways to style code with GitHub's markdown. If you have inline code blocks, wrap them in backticks: `var example = true`.  If you've got a longer block of code, you can indent with four spaces:

    if (isAwesome){
      return true
    }

GitHub also supports something called code fencing, which allows for multiple lines without indentation:

```
if (isAwesome){
  return true
}
```

And if you'd like to use syntax highlighting, include the language:

```javascript
if (isAwesome){
  return true
}
```

# Table

First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column

# Extras

GitHub supports many extras in Markdown that help you reference and link to people. If you ever want to direct a comment at someone, you can prefix their name with an @ symbol: Hey @kneath — love your sweater!

But I have to admit, tasks lists are my favorite:

- [x] This is a complete item
- [ ] This is an incomplete item

When you include a task list in the first comment of an Issue, you will see a helpful progress bar in your list of issues. It works in Pull Requests, too!

And, of course emoji! :sparkles: :camel: :boom:

# Underscored variable(WebFundamentals)

project_path: /web/_project.yaml
