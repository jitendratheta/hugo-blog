---
title: "Publishing website using Hugo and Github Pages"
date: 2021-02-25T08:16:46+05:30
draft: false
tags: ["blogging", "web hosting"]
categories: ["web"]
author: "Jitendra Kushwaha"
---
## Introduction

This tutorial will show you how to host your website using Hugo and Github Pages. Github pages allows you to host static content directly via repository in github. 


## Hugo Installation
Open your terminal, run the following command-line one by one:

```
brew install hugo
```
To check whether you installed Hugo successfully, enter the following into your terminal

```
hugo version
```
Here is output will look like

```
[25/02/21 22:07:16] ➜  ~ hugo version
hugo v0.81.0+extended darwin/amd64 BuildDate=unknown
```

## Build Local Site

The first step is to go to the directory where you want to save your website, I want to create my site on my desktop, so run the following command in terminal.

```
[25/02/21 22:11:46] ➜  ~ hugo new site helloWorld
Congratulations! Your new Hugo site is created in /Users/jitendra/helloWorld.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```
The folder struture will look like this

```
[25/02/21 22:13:00] ➜  ~ cd helloWorld
[25/02/21 22:13:03] ➜  helloWorld tree
.
├── archetypes
│   └── default.md
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes

6 directories, 2 files
[25/02/21 22:13:05] ➜  helloWorld
```
The ones we will work with:
- config.toml : the configuration file, we will need to edit it later.
- content : stores all the content of the website, including all of your blog posts, resumes and so on, can include folders, but usually all .md files.
- static : Stores static files such as your background pictures, logos, css, js, etc. The files in this directory will be directly copied to it /public. This folder has higher priority than the /staticfolder under the theme.
- themes : now it’s empty, but will save the theme of your choice later.

The others, but we will not use them in this tutorial:
- archetypes : stored .mdtemplate files, it has higher priority than /archetypesfolders under the theme.
- data : stores data files for template calls
- layouts : store .htmltemplates, this folder has higher priority than /layoutsfolders under the theme

Also, there will be a “public” folder created when you want to deploy the website:
- public : After executing the hugocommand, store the generated static file

Choose a theme

Pick a theme you like from the official website [Hugo themes](https://themes.gohugo.io/) or from Github ( You can find the source themes from people’s Repository)!

```
[25/02/21 22:23:26] ➜  ~ cd helloWorld
[25/02/21 22:23:27] ➜  helloWorld git init
Initialized empty Git repository in /Users/jitendra.shivnarayan/helloWorld/.git/
[25/02/21 22:23:31] ➜  helloWorld git:(master) ✗ git submodule add https://github.com/olOwOlo/hugo-theme-even themes/even
```

update your local config.toml with [config.toml](https://github.com/olOwOlo/hugo-theme-even/blob/master/exampleSite/config.toml)

Create you first blog

```
[25/02/21 22:26:29] ➜  helloWorld git:(master) ✗ hugo new about.md
/Users/jitendra.shivnarayan/helloWorld/content/about.md created
```

Test the site locally by running command:

```
[25/02/21 22:28:01] ➜  helloWorld git:(master) ✗ hugo server -w
port 1313 already in use, attempting to use an available port
Start building sites …
WARN 2021/02/25 22:28:08 found no layout file for "HTML" for kind "home": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2021/02/25 22:28:08 found no layout file for "HTML" for kind "taxonomy": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2021/02/25 22:28:08 found no layout file for "HTML" for kind "taxonomy": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.

                   | EN
-------------------+-----
  Pages            |  3
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  0
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0

Built in 7 ms
Watching for changes in /Users/jitendra.shivnarayan/helloWorld/{archetypes,content,data,layouts,static}
Watching for config changes in /Users/jitendra.shivnarayan/helloWorld/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

Content of about.md will be available at [http://localhost:1313/about](http://localhost:1313/about)

Local website will look like this
{{< figure src="/post/media/local_site.png" title="local site" >}}

##  Creating Github pages

Below is github pages tutorial from Github.

{{< youtube 2MsN8gpT6jY >}}

Head over to [GitHub](https://github.com/) and create a new [public repository](https://github.com/new) named username.github.io, where username is your username (or organization name) on GitHub.
If the first part of the repository doesn’t exactly match your username, it won’t work, so make sure to get it right.

{{< figure src="/post/media/create_repository.png" title="Create Repository" >}}

Copy paste the `public` folder data from local site to root of the repository and push the changes
