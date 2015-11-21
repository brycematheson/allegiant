+++
title = "My love-hate relationship with WordPress"
date = "2014-12-06T18:50:20-07:00"
+++
Recently, I’ve really been getting fed up with WordPress. And here’s why.

WordPress dates all the way back to 2001. It was originally developed as a simple blogging platform based off of MySQL and PHP. Close to fifteen years later, it’s become a web standard and is used as the Framework/CMS for <a href="http://en.wikipedia.org/wiki/WordPress" target="_blank">more than 20% of all the websites on the internet</a>. And that’s exactly the problem.

WordPress has exploded into a million different forks and subprojects, and has been expanded to run an equal amount of themes and plugins. My biggest issue with this is that WordPress was never *designed* to support this. Years down the road, it’s still sitting on code that dates back a decade. The same issue holds true with Microsoft. Even after launching Windows 8.1, it still has pieces of code that were used in the Windows 3.1 and Windows 95 operating systems. It baffles me that 20 years later, we still can’t seem to ditch MS-DOS or the Registry.

WordPress was never designed to be used as an e-commerce platform, but with the help from the guys over at <a href="http://www.woothemes.com/woocommerce/" target="_blank">Woocommerce</a>, it’s never been easier and quicker to do so. WordPress was never designed to be used as a Social Media platform, but of course, there are plugins to do that as well. WordPress is so simple and easy to use, that it’s become overly bloated with features to cater to the needs of everyone. I fear that it’s soon going to crumble in on itself.

## Security Holes

And here’s something else to think about too. Even if only 1/100th of all websites on the internet were using WordPress as their CMS, imagine what would happen if a large exploit wereÂ found. Millions of websites are instantly vulnerable in the hands of skilled hackers. Sadly, the number of potential targets isÂ a lot larger than 1%, should an exploit be found. Many users don’t know that they would be perfectly fine completely ditching the database, and just using static HTML to host their blogs, completely eliminating the security flaws.

## Updates

WordPress updates are the absolute worst. Starting somewhere in the time-frame ofÂ Wordpress 3, automatic updates were introduced by default (although you can turn these off through the database, I believe). For a lot of the websites I build and manage for clients, I set myself up as an administrator. Whenever an automatic update is pushed, I get an email saying, “Your WordPress installation has been updated to version 4.0.1…” I cringe just thinkingÂ about all the hundreds of things that could now be broken on dozens of my websites. Granted, the WordPress team does their absolute best to ensure that nothing breaks, but with hundreds of thousands of different themes and plugins, how can anyoneÂ be absolutely certain that they won’t be a compatibility issue somewhere?

## Comments

The comment system in WordPress is so flawed, it’s not even funny. Even when using a plugin to block/prevent spam, there are times when I’ll log into my dashboard and find that I have 300+ pending comments to be approved, 90% of them being complete garbage. What’s even more annoying is that all of these comments, whether legitimate or spam, are being stored in the database, ultimately slowing down the over-all speed of your website.

## Speed

Touching on this already a little earlier, having a backend attached to any website is most always going to ensure a decrease in speed unless it’s closely managed and optimized. Most of the time, the end-user has little to no knowledge on how to do this. Many users would be perfectly fine serving plain ol’ static HTML or using a static site builder such as <a href="http://jekyllrb.com" target="_blank">Jekyll</a> or <a href="http://middlemanapp.com" target="_blank">Middleman</a>. Every query to a database requires more bandwidth, and more server strain.

I’m a little hesitant to even touch on the topic of themes, because it irritates me so much. The other day I was looking at some of <a href="http://themeforest.net/search?utf8=âœ“&term=&view=list&sort=sales&date=&category=wordpress&price_min=&price_max=&sales=&rating_min=&platform=" target="_blank">the best-selling WordPress themes on themeforest</a>. These themes, in my opinion, are so poorly coded, and so irritatingly slow. The builders of these themes attempt to cater to everyone and no one, all at the same time. Do they have any training about UI or UX? Do they understand that they need to minimize their CSS and JavaScript? Do they understand that they need to optimize their images to a suitable web size? Clients come to me and say, “Oooh. I like this look.” They truly have no idea what they’re doing. Having something that looks “pretty” just won’t cut it. There’s a lot more to think about behind the scenes, rather than just how a website looks.

I’ve seen theme packages that, for the entire install, run in the area of 15 megabytes. 15 MEGABYTES!? Are you kidding me? Even with LTE cell phone speeds and fiber-optic internet connections, 15 megabytes is a lot of data. Good luck having users stick around when your site won’t load on their phones. Some people might say, “Well, users will wait for at least a second for my site to load.” Wrong. <a href="http://www.fastcompany.com/1825005/how-one-second-could-cost-amazon-16-billion-sales" target="_blank">Amazon did a study</a> on page load speed, and how it affects their sales conversion rates. They found that a one-second difference in page-loading speed could cost them up to $1.6 Billion in sales.

## The Art of Web Design

In my mind, building a website truly is a work of art. I’m proud of the hours that I’ve spent in learning, growing, and honing my skills in order to develop something out of thin air that helps a client’s business or hobby or whatever. However, nowadays, it seems that we’re beginning to lose that art in development. Websites such as <a href="http://www.wix.com" target="_blank">wix</a>Â make it seemingly so simple to throw up a website that anyone can do it. WordPress is no different. Now, because of the simplicity of WordPress, people begin calling themselves “Developers” or “Experts” without even touching a single line of code.

## Ease of Clients

Now, here comes the love. I really don’t hate WordPress, although it may seem that way. One of the number one reasons I use WordPress as a CMS for my entire client base is the ability to entirely hand of a project. We’ve all worked with clients that are annoying, nagging, and constantly changing their mind. When the project is done, I can’t wait to get “rid” of them, because it’s a never-ending project. Nothing ever gets finished. WordPress allows me to (finally!) finish a project and give them the ability to change and manipulate virtually anything they may want with knowing little or no code at all, and best of all, without involving me.

## Quick and Inexpensive

When you’re constantly beginning new projects, you get in the habit of building your own mini-framework, in hopes to cut off some of the development time or shave off some of the repetitiveness. WordPress is KING of saving time. I can create a new hosting environment, and have a functional WordPress installation in less than five minutes total. Then, I can focus on the needs of the customer and the design, rather than re-inventing the wheel for the 500th time.

## Conclusion

Ultimately, I think my hatred really comes down to the bloat of WordPress. It reminds me so frequently of those who attempt to build an entire website using Dreamweaver’s visual mode. Yes, it’s possible to do it without knowing any code at all. But if you know anything about code, you can instantly look at the code that Dreamweaver spits out, and you know how much bloat and garbage can be cut out. WordPress is an incredible piece of software, and that’s apparent in it’s widespread usage. But bloat is my number one concern.

If you’re familiar with <a href="https://developers.google.com/speed/pagespeed/" target="_blank">Google’s Page Speed</a> analysis, you might be surprised to see that even some of the most popular websites rarely score above 50%. Take a basic WordPress theme, give it a test, and you might be surprised that you only received a score of 27. Developing everything from scratch, you can easily shave off the bloat and improve your page speed, which can equate to improved SEO through Google.

One last point, and then I’ll shut up. Am I using WordPress to run my blog? Absolutely. Is there a lot of bloat? Maybe a little, but I’ve tried to cut out everything that I could. I’m scoring in the 90’s in most aspects of Google’s Page rankings. I think I fall into the trap that so many other users do, and try too hard to focus on design, colors, and appearance, and not so much on the content. I was recently inspired by <a href="http://davidbcalhoun.com" target="_blank">David Calhoun’s blog</a>, and have since changed the design of my own blog to a more minimal design. David’s blog is great. It’s plain, clean, crisp, but more important, it’s fast. It provides the required functionality, and then the rest is focused on the content. Does David’s readers care that his blog is plain? Not really. He has a consistent reader-base, because of what he provides. Rarely, if ever, would anyone say, “This is a great looking site. I’m going to come back, even if there’s nothing here for me.” No. Does a good design/functionality help? Of course. But it’s not everything.