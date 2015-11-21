+++
title = "Take that, Mr. Barney"
date = "2014-12-20T18:50:20-07:00"
+++
We've all had those professors/teachers that we just don't seem to mesh with. Recently, I had a professor with whom I could *not* set aside my differences. The class was about Mobile Application Development. I went into it thinking, &#8220;Wow, I'm excited! Finally, I'll be able to create an iOS/Android application!&#8221; On the first day of the class, Mr. Barney walked in and said, &#8220;This is not a programming class. This is not an iOS development class. This is not an Android development class. This class has no tests. This class has no assignments. This class has no texts, no books.&#8221;

As the class progressed, I got more and more frustrated with the structure and Mr. Barney's teaching style. It seemed that the class was more about learning Mr. Barney than it was about the material. He came off as a close-to-retirement professor with a God-complex, who was tired of his job, and was just coasting on his measly salary for a few more years until he could finally escape.

The class consisted of a few technologies that we were forced to learn on our own, namely HTML 5, CSS Animations and Transitions, AJAX, DOM Manipulation, JavaScript Basics, etc. Because there were no class materials, we resorted to YouTube tutorials and blog articles to learn. On a bi-monthly basis, we would meet one-on-one in his office and present some sandbox code that we had been playing with that demonstrated one or more of these technologies. Based on his mood that day, he would open a little spreadsheet and rate you anywhere from &#8220;Strongly Disagree&#8221; to &#8220;Strongly Agree,&#8221; which ultimately equated to your class grade.

At one point, I decided to bring in a simple sandbox weather application, using an AJAX call to link to an API and populate data into the DOM based on the user's location. The application used JQuery. While looking at my code, the second he saw a reference to JQuery, he tore it to *pieces.* &#8220;JQuery is of the devil.&#8221; or &#8220;JQuery is only for lazy programmers.&#8221; and &#8220;What happens if the JQuery library breaks, what happens to your application?&#8221;

Okay, so, maybe he didn't say, &#8220;JQuery was of the devil.&#8221;

Basically, his point all boiled down to this: You can use JQuery, but it's a bloated library and it contains so many additional pieces that you don't need, and ultimately, you can do exactly what you need with plain ol' vanilla JavaScript. It's slow, and it would take a long time to download the entire library, when you don't need it.

For the rest of the class, I hated him for it. 9 times out of 10 as I left his office, I was fuming. And I really do understand his point, and I believe that it has *some* validity, but mostly, it's just him being old and outdated, and stuck in his ways.

Even after finishing the class, I hated him for it. Have you tried looking for web tutorials online for advanced AJAX calls that don't use JQuery? It's *impossible*!

In case you hadn't noticed (as in, you aren't using this website on a mobile device), the top navigation bar uses JQuery to convert to a small menu icon on smaller screens. I wanted to prove to myself that JQuery really isn't *that* bloated, and that it is in fact a useful tool, and better than writing vanilla JavaScript.

After playing with a few things, I finally got the results I was looking for. Check out the results that I got while using <a href="http://tools.pingdom.com/fpt/" target="_blank">Pingdom Page Speed</a>. More specifically, look at the red box. My &#8216;styles.css' file (that isn't minified, btw) weighs a whopping 6.2kB. JQuery, which is more than 6x larger, loads more than twice as fast. How did I do it?

<img src="/img/post_images/pingdom-speed-results.jpg" alt="Pingdom PageSpeed Results" />

If you're familiar with Bootstrap, and the way that you can customize it just to your liking, JQuery is the same. Usually, whenever I use Bootstrap, I don't need all the font icons or navigation bars, or any of that. I only use the responsive pieces. With JQuery, they have similar options on their website to where you can customize it to your liking. I knew that the only piece I'd be using on my website is the navigation library. So I stripped everything else out.

Also, up until this point, I wasn't familiar with CDNs, or the power that they potentially had. Pulling JQuery from their hosted CDN, rather than from my on my own shared web server undoubtedly speeds up the page load. My website is pretty barebones, and that's done on purpose to increase page speed. Loading times have come into consideration for everything I do on this site, but I don't feel that JQuery has in anyway been detrimental to that.

I feel justified. Take that, Mr. Barney! </rant>