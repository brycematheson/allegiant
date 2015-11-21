+++
title = "Visual Form Builder PayPal Redirect"
date = "2014-10-03T18:50:20-07:00"
+++
For anyone who knows me even slightly well knows that I’m a huge fan of WordPress. I use it as my go-to CMS for all of the websites I create, whether for myself or for clients. It gives me the flexibility I need in a well designed format, and it gives my clients the ability to make changes to their own websites without knowing any code.

Some people will give you a giant list of plugins that you have to download when first setting up your WordPress site. My theory is the opposite. The fewer plugins, the better. I don’t install something if I don’t need it, just to have it. One plugin I almost always find myself installing, though, is <a href="https://wordpress.org/plugins/visual-form-builder/" target="_blank">Visual Form Builder</a>. It makes creating HTML forms a piece of cake. Sure, you can code them all yourself, but why when this is so easy? It offers plenty of features, such as sending a copy of the form to administrators, to the person filling out the form, and so many other features. There is a <a href="http://vfbpro.com/" target="_blank">Pro version</a> as well if you need it, but I’ve found that all the features I need are offered in the free version.

One thing I often do for clients is build a form using this plugin so that they can collect some data or information from their customers. Once the customers click “Submit” on the form, it redirects themÂ to a PayPal link where they can purchase a product. All of this is done through Visual Form Builder. On the “Confirmation” section, you have the option of redirecting the user to a different page in your WordPress site, to a different URL, or just display some text. Here is where I select “URL” and then post in the link that (under the email tab, not the WordPress form code) that PayPal has given me.

This morning, however, I ran into a new problem I’d never seen before. Upon redirection, I saw this error through PayPal:

<img src="/img/post_images/visualformbuilder1.png" alt="Visual Form Builder" />

I did everything that I could think of, and I could not for the life of me figure out the issue. It kept saying that I was missing “required information”. The thing was that I wasn’t sending any information. And what was even more baffling was that if I copied the link directly into a browser, the URL worked fine, and I was successfully redirected to PayPal. Therefore, the problem lies with Visual Form Builder.

I scoured the internet. I found a post on the plugin support page with someone having the same issue as me, but it was a quick dead-end. It was over 2 years old, and no problem had been found. The developer basically said, “Buy the Pro version.” And then the topic was closed. Well, that was no help.

I continued trying. After a lot of trial and error, I finally found a workaround. I used the <a href="https://goo.gl/" target="_blank">Google Link Shortener</a>, and for some reason, that worked. I pasted in my PayPal “email” link, and then Google spit out a shorter URL. I pasted that into the “Redirect” field under the confirmation settings, and voila! It worked!

<img src="/img/post_images/visualformbuilder2.png" alt="Visual Form Builder" />

This seemed to work for me. It’s not ideal, but it’ll do for now. Have you had a similar problem? Does this work for you? Let me know what you think.