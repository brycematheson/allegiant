+++
Description = ""
FeaturedImage = "/img/plane.jpg"
Tags = []
date = "2015-11-22T10:54:54-07:00"
title = "Allegiant Features"

+++

# Allegiant -- A kick-ass Hugo theme
Allegiant has all sorts of cool stuff. You can include a per-post background image by editing the "Featured Image" section in the post header data.

# Custom Config
It's got custom data you can edit in the config.toml file too. Here's a sample:

~~~toml
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
~~~

## Auto Syntax Highlighting for any language
It's got built in Syntax highlight, too. Just start a block of code with "~~~typeyourlanguagehere" and then close it with three more squiqlies. If you view the above block of code in a text editor, you'll see what I mean.

## Code Snippets
In case you don't want to do an entire block of code, you can just do a small snippet of code, such as a command to type in, or a key to press by wrapping your text in a span class of "smallcode". <span class="smallcode">This is what it'll look like.</span>

## Sharing Icons
Sharing icons are automatically embedded in the post. So that's cool.

## Fast
Gets a 73/100 ranking on Google PageSpeed Insights. And that's WITH render-blocking CSS, and no CDN. Fix those things, and you'll hit a 95/100.

## More
There's a lot more this theme can do, and it's really cool, but I'm really hungry and going to go eat lunch. So I'm going to upload this to GitHub and be done with it.