# Allegiant

## Overview

A demo of the theme can be seen by visiting my blog at www.brycematheson.io.

Allegiant is a simple and clean blog theme for [Hugo](http://gohugo.io/). Some of the more notable features are:
- Super simple/clean design
- Client side source code highlighting (using Highlight.js)
- Social links (Twitter, Facebook, GitHub, LinkedIn, etc)
- Analytics with Google Analytics
- Responsive
- Font Awesome icons

![Allegiant Screenshot](https://github.com/brycematheson/allegiant/blob/master/images/screenshot.png)

## Installation

In your hugo site directory, run:

```shell
$ mkdir themes
$ cd themes
$ git clone https://github.com/brycematheson/allegiant
```

## Configuration

You may specify following options in `config.toml` of your site to make use of
this theme's features.

```toml
baseurl = "yoursitehere.com"
languageCode = "en-us"
title = "Allegiant"
copyright = "&copy; Allegiant. All Rights Reserved." # Copyright notice. This will be displayed in the footer.
canonifyurls = true

[params]
    ga_api_key = "Your Google Analytics tracking id" # Google Analytics API key.
    avatar = "../../img/avatar.jpg" # Image should be square, and roughly 150px x 150px
    bio = "Insert your bio here. You should write something really whitty and interesting that nobody is ever going to read or care about. But such is life. I really like the look of having a bio snippet on the blog, though. You may have to adjust some CSS styles depending on how long or short your bio is. I didn't make it super resillient."
    github = "http://github.com/username"
    twitter = "https://twitter.com/username"
    linkedin = "https://www.linkedin.com/in/username"
    footer_1 = "Some text here."
    footer_2 = "Some different text here."
    footer_3 = "Even more different text here."
```

