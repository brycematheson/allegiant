# Allegiant

## Overview

Allegiant is a simple and clean blog theme for [Hugo](http://gohugo.io/). Some of the more notable features are:
- Super simple/clean design
- Client side source code highlighting
- Social links (Twitter, Facebook, GitHub, LinkedIn, Instagram, etc.)
- Support for tags
- Analytics with Google Analytics
- Responsive
- Font Awesome icons

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
baseurl = "Your site URL"
languageCode = "en-us"
title = "Allegiant"
copyright = "&copy; Allegiant." # Copyright notice. This will be displayed in the footer

[params]
    # Social accounts. Links to these accounts are displayed in the header and footer.
    twitter = "Your Twitter username"
    github = "Your GitHub username"
    linkedin = "Your LinkedIn username"
    googleplus = "Your Google+ user id"
    facebook = "Your Facebook username"
    # stackoverflow = "Your Stackoverflow user id (number)"
    # keybase = "Your keybase.io username"
    # instagram = "Your Instagram username"
    # Disqus shortname
    disqus = "Your disqus shortname"
    # Google Analytics API key.
    #ga_api_key = "Your Google Analytics tracking id"
    author = "Bryce Matheson"
    avatar = "/path/to/avatar"
    contact = "Your contact link (ex. mailto:foo@example.com)"
    bio = "Your short bio"
    # Short subtitle/tagline. This is displayed in the header.
    subtitle = "Short subtitle/tagline of your blog"
```

