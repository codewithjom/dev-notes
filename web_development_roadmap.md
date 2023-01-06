# Web Development Roadmap

## Table of Contents

- [Start Learning Web Development Today!](#org41eda7a)
  - [1. Foundations of Internet](#orgbd3eaa4)
  - [2. Code Editor](#org43b65bc)
  - [3. Git and GitHub](#org4106338)
  - [4. HTML](#org3eff62c)
  - [5. CSS (Cascading Style Sheets)](#orgcdef388)
  - [6. JavaScript](#orgcc045bf)
  - [7. Deployment](#orgaec28dc)
  - [8. What to learn next?](#org4588383)

<a id="org41eda7a"></a>

# Start Learning Web Development Today!

There are many web development roadmaps produced by different developers so let me offer my own as well.

If you are thinking about getting into web development, I recommend you learn/watch at least a few of those roadmaps and then make up your mind what you want to learn.

Everybody will have a different opinion on what is the best technology, language or framework. You should also follow your heart and go in the direction that feels right for you.

You may be scared when you see some of these roadmaps. Well, even with many years of web developement experience, I'm also scared when I see some of them.

That's why in this article I'm going to offer you my simple but complete version of the web development roadmap for absolute beginners and the essential things you need to learn first.

After this initial stage of learning the basics, you will know what to learn next and even if you like web development at all.

So this is a web development roadmap for 2022 in the most simple way that I can put it.

Learning anything, especially complex web development, can be a daunting task so we don't want to spend too much time on unnecessary details at this stage and we want to make it as much fun as possible and progress quickly.

<a id="orgbd3eaa4"></a>

## 1. Foundations of Internet

You don't need to spend a lot of time here if you know the basics like domain name, DNSs, servers, web browsers, hosting.

When I say basics I mean basics.

You just need to know what these things are and what they do and without wasting any unnecassary time you can move on.

You are learning web development and Not DevOps and you will learn more if you need it on the topic later along the way.

<a id="org43b65bc"></a>

## 2. Code Editor

Now, Visual Studio Code (VSC) is not the only code editor out there and you are free to find and use a different one, some developers will recommend to use VSC in Web Development but for me I use GNU Emacs as my code editor.

VSC is the most popular code editor these days for web developers while on the other hand GNU Emacs is an extensible, customizable, free text editor and more. For me, GNU Emacs is not only a text editor, it can do anything what you want and by configuring GNU Emacs it uses Emacs Lisp (a programming language) which is not recommended for beginners. But if you are reading this using GNU Emacs you are in the right place!

- [Download](https://code.visualstudio.com/Download) the Visual Studio Code and install it on your computer.
- [Download](https://www.gnu.org/software/emacs/download.html) the GNU Emacs and install it on your computer.

If you are interesting using my own configuration of GNU Emacs [check](https://github.com/codewithjom/dotfiles/tree/master/.emacs.d) my repository, every line of code has a description on it so that you can understand what the code do.

Familar yourself with the interface and the basics shortcuts (creating a new file, closing the file, saving the file, etc.).

You can spend more time here if you want and watch some tutorials and courses on VSC but you don't need to do it. You will learn more along the way.

<a id="org4106338"></a>

## 3. Git and GitHub

Git is a free and open-source version control system. It is industry standard and as a web developer, you must know it.

The idea of Git is to track changes in the code and it also enables many developers to seamlessly work on the same project.

GitHub, on the other hand, is a code repository in the cloud where you can store you Git code in a private or public repository.

<a id="org3eff62c"></a>

## 4. HTML

Now we're getting into web languages that will actually enable you to create website and we have to start from HTML.

HTML is not a programming language but it is HyperText Markup Language. It is the most popular language on the web and every website uses it. That is why without HTML you cannot be a web developer and that is why we start from learning it.

Simple HTML code look like this:

``` html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>HTML</title>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
  </head>
  <body>
    <p>Hello World!</p>
  </body>
</html>
```

HTML is quite broad language but at this stage you just need to learn the basics.

- the stucture of the document: `<html>`, `<head>`, `<body>`
- head section: `<title>`, `<meta>`, `<link>`, `<script>`
- body section: `<div>`, `<p>`, `<a>`, `<img>`, `<strong>`, `<em>`, `<ul>`, `<ol>`, `<li>`, `<table>`, `<tr>`, `<td>`, etc.
- semantic html: `<header>`, `<footer>`, `<nav>`, `<article>`, `<main>`, `<section>`, `<aside>`
- html attributes: `id`, `class`, `src`, `alt` and others.

There are many more HTML tags but to start you just need to learn these basics as they are most commonly used. You can find the details of those and more about HTML by watching Youtube HTML Crash Courses!

I also have a repository in GitHub where I wrote a full course of HTML, CSS and JavaScript and many more to come! [Click](https://github.com/codewithjom/OrgBook) to visit the repository I recommend to read them in your GNU Emacs if you have them else, I will be posting them on my website soon!

<a id="orgcdef388"></a>

## 5. CSS (Cascading Style Sheets)

CSS is another essential language of the web that every website is using.

It gives developers and designers ability to specify fonts, color, positions, and other aspects of elements on the website. It is also used to create responsive websites (websites that work on devices with different size like desktops, tablets, mobile phones).

At this stage I would recommend learning the basics of CSS because otherwise it is easy to feel overwhelmed. Unless, you'll find it particularly interesting. Then you can spend a little bit more time here.

What you definitely need to know in terms of CSS:

- how to add on-page, inline and external CSS
- IDs, classes and how to target HTML elements in general with CSS so you can style them; it is quite an advanced topic on its own to properly target HTML elements with CSS; you have different ways to target HTML elemtns, by tag name e.g. div, by ID or by class name; also, HTML elements and classes can be nested so pay close attention to this aspect of CSS you can easily get lost.
- font size, line height, font decoration, how to add color and hexadecimal color names.
- margin, padding and in general CSS Box Model
- border, opacity, backgrounds
- pseudo-classes (:hover, :active, :focus, :first-child, :last-child, :nth-child)
- CSS positioning (position absolute, relative, top, bottom, left, right, etc.)
- CSS grid layout (two-dimensional grid system to CSS)
- CSS flexbox (one-dimensional layout model)

These are just the basics but feel free to dig depper as you need.

I also have a repository in GitHub where I wrote a full course of HTML, CSS and JavaScript and many more to come! [Click](https://github.com/codewithjom/OrgBook) to visit the repository I recommend to read them in your GNU Emacs if you have them else, I will be posting them on my website soon!

<a id="orgcc045bf"></a>

## 6. JavaScript

Finally, a programming language, JavaScript.

JavaScript is a scripting language, the most popular language on the web, that runs in the web browser.

It is often used for the dynamic functionality of the website like showing or hiding elements on mouse click, animations, displaying dynamic and interactive elements like timers, drop-down menus, requesting additional information from another website/api, form element validation etc.

JavaScript is also used for building entire applications or as a back-end programming language but at this stage, we just want to learn the basics.

What you definitely need to know it terms of JavaScript:

- Types and variables
- Scope
- Assignment, arithmetic, comparison and conditional operators
- If and switch
- Functions, break, continue
- For loops, break and continue
- Objects, JSON
- Events
- DOM manipulation

I also have a repository in GitHub where I wrote a full course of HTML, CSS and JavaScript and many more to come! [Click](https://github.com/codewithjom/OrgBook) to visit the repository I recommend to read them in your GNU Emacs if you have them else, I will be posting them on my website soon!

<a id="orgaec28dc"></a>

## 7. Deployment

Once you have your project on GitHub, which is something that you should do for every project, deployment should be straightforward.

You can use [Netlify](https://www.netlify.com) or [Buddy](https://buddy.works) for example to deploy and make your project live directly from GitHub.

For more advanced deployments, tools like [DeployHQ](https://www.deployhq.com) or [CircleCI](https://circleci.com) can be used.

For hobby or small projects all these options will be free.

<a id="org4588383"></a>

## 8. What to learn next?

Now you are familar with the basics of web development and you have employable skills, yes, after you have completed these steps you know the whole web development workflow and you are able to create a website from start to finish. This enables you to start looking for a job as a junior web developer, while continuing improving your skills or start working on web projects as a freelancer which is also great option for a start.

But what to learn next to take things to the next level?

- **Figma, Sketch or Adobe XD** - sometimes you may need to code a website in HTML, CSS and JavaScript based on the design. These are probably the most popular design tools these days so it is a good idea to learn them.

- **Advanced JavScript** - once you know the basics of JavaScript it is a good idea to keep learning more advanced concepts like closures, Object Oriented Programming, Asynchronous JavaScript and others.

- **Bootstrap 5** - open source front-end tool that enables quick development of responsive websites.

- **JavaScript Framework (React, Vue.js, Angular, Svelte)** - learn one of these JavaScript Frameworks, React and Vue.js are by far the most popular but take a look also at other frameworks.

- **Backend language (PHP, Python, Node.js)** - if you want to become a full-stack developer then it is essential to learn a backend language and framework. Check available options and learn the one you feel most comfortable with. As you already know JavaScript a bit, Node.js might be your preffered choice here.

- **Databases (MySQL, MariaDB, PostgreSQL, MongoDB)** - more advanced projects require some kind of database to store user information and other website data. Therefore familiarising yourself with at least one databse engine and SQL (Structured Query Language) is essential.

- **Regular Expressions** (pattern matching in text) - commonly used in all programming languages.

- **APIs (working with third-party applications and databases)** - as a web developer you will work a lot with APIs pulling information or sending information to third-party applications. Therefore working with APIs should be on you things to learn as soon as you can.

The list goes on but as you learn you will come across new technologies, languages and frameworks so it is a good idea to keep a list of things you want ot learn next and update it regularly.

You can choose to specialise in one thing, like JavaScript and React, or learn many different technologies which will give you more flexibility and enable you to work on projects as a full-stack web developer or freelancer.
