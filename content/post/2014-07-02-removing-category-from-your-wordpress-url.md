+++
title = "Removing 'category' from your WordPress URL"
date = "2014-07-02T18:50:20-07:00"
+++
There's no doubt about it. WordPress is popular, easy to use, and here to stay. It's estimated that more than 20% of the internet is currently running on the CMS. With drag-and-drop features, thousands of themes, and super-simple customization, it's easy to see why. That doesn't mean WordPress doesn't come without any quirks, though.

One of those many quirks (annoyances, really) are the &#8216;categories' feature. While it's a piece of cake to categorize posts into various sections, there's always been one thing that has bugged me. In your browser, underneath a specific category, the URL will always look something like this: "http://www.mysite.com/category/agriculture". Have you ever wanted to get rid of the &#8220;category&#8221; piece so that your url simply looks like this: "http://www.mysite.com/agriculture"?

It's actually quite simple to do. If you're a fan of plugins, you can use the <a href="https://wordpress.org/plugins/fv-top-level-cats/" target="_blank">FV Top Level Categories</a> plugin. There's no configuration, no settings. Just activate the plugin, and you're ready to go. Now, with that being said, I'm not against plugins by any means, but if I can find another way around, I'll usually take that route.

### Option 2

You can simple change the settings under your permalinks in WordPress. In WordPress, on the left side menu, go to \*\*Settings &#8211;> Permalinks\*\*.

Under &#8220;Custom Structure,&#8221; enter &#8220;`/%category%/%postname%/`&#8221;. Also, enter a &#8220;`.`&#8221; under &#8220;Category base&#8221; as shown below in the photo.

<img src="/img/post_images/permalinks_wordpress.png" alt="RAID" />

Select &#8220;Save Changes&#8221;, and you should be good to go. From my experience, this hasn't broken any links, and everything works as it should. While this works for now, there's no telling if any future updates or upgrades to WordPress can or will break this.

Happy tweaking!