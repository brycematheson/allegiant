+++
title = "Pseudo-Responsive Images"
date = "2014-12-15T18:50:20-07:00"
+++
Honestly, I'm a bit embarrassed to say that I didn't know how to do this before. I'll be creating a blog post here fairly soon on my conversion from WordPress to Jekyll for this blog, but in doing so, I've learned a lot of cool new things.

Due to the vast number of mobile devices in circulation right now, I make it a habit to try and develop for mobile first, and then expand for the desktop user. Developing for mobile almost instantly implies responsive design. There are dozens of CSS frameworks to do this (Bootstrap, Foundation, Skeleton, etc.) intended to make your job a little bit easier.

I ran into an issue while coding this site. My content would all scale down properly and fit into the viewport perfectly, except for images, which would overflow the bounds of the viewport. I couldn't for the life of me figure out what I was doing wrong. When copying content over from WordPress, I guess that I had added &#8216;width' and &#8216;height' attributes, which forced the images to display at those dimensions. After going through all of the images and removing both of those attributes, I simply went to my stylesheet and added the following. Lucky for me, I didn't have too many images to go through:

~~~css
img {
  width: 100%;
  box-shadow: 10px 10px 5px #888888;
}
~~~

Obviously the box-shadow isn't required, but I just like add it for aesthetics.

That selects all images across my entire website, and tells them to stretch to 100% of the viewport (which, in the case of this site, is 700px). As the page resizes, or is viewed on a different viewport size (such as a phone or tablet), that image is scaled down accordingly.

One thing to mention, too, is that if you remove just the &#8216;width' attribute, but leave the &#8216;height' attribute, your images will come out all stretched and skewed as the image is scaled according to the viewport size.

It's also important to note that this isn't the &#8216;real' way to present responsive images on your site, I'm just too lazy to do it the <a href="http://css-tricks.com/responsive-images-youre-just-changing-resolutions-use-srcset/" target="_blank">real way</a>. This way works perfectly for me, until it becomes simpler.