+++
title = "Static Site (Database Free) Contact Form"
date = "2015-01-19T18:50:20-07:00"
+++
Although my site is always a work in progress, (I've still got plenty of things I need to do on it), I feel like it's in the final stages. Recently, I was trying to add the finishing touches by implementing a contact form. Mostly, to combat spam. I didn't want to throw my direct e-mail address out there, because that's just asking for an inbox full of viagra ads.

The thing that I wanted to completely avoid was having any server-side (PHP) scripting, or databases. With most contact forms, that's a inevitable. But my main concern with just about everything on my site is performance. I wasn't willing to add a database just for that. So I went searching.

Introducing <a href="http://formspree.io/" target="_blank">Formspree.io.</a> It's crazy easy. It involves using code, so if that scares you, you might want to stay away. But really, it's just simply copying and pasting that anyone can do it. Besides, if you're not into code, what're you doing reading my blog?

Basically, you place their code on your site, and when someone submits anything in the form, all of the processing is done on their servers and forwarded to an email address that you provide. And what I love is that their logo isn't plastered all over the place. It's super minimal, and you don't even have to register an account with them.

~~~html
<form action="http://formspree.io/youremail@pasteithere.com" method="POST">
  <p>Email:</p><input type="email" size="40" name="_replyto">
  <p>Message:</p><textarea style="border: 1px lightgray solid; width: 100%; height: 300px;" name="body">
  </textarea><br/>
  <input style="display: block; width: 125px; text-size: 20px;" type="submit" value="Send">
</form>
~~~

All you have to do is replace the `youremail@pasteithere.com` with the address you want your submissions to be forwarded to. Throw that on your site. The first thing you have to do is submit a test form, and a confirmation email will be sent to the address you specified. Once it's confirmed, you're set to go!

I left all the styling that I used in my form for you to use. You can strip it out or do whatever you want with it, obviously.

You might be wondering about costs or privacy. Right now, there's a 1000/month cap on emails. Anything above that and you'll have to pay, but I'd be surprised to get even 20 submissions a month from legitimate sources on my own site. As far as privacy, they say that don't store any of the contents of the submissions, because they're using the Mailgun API. And even if they did, I'm not too worried about it. You shouldn't be submitting sensitive data to an unsecure form on the web anyway.

One of my favorite features is the ability to add a &#8220;honeypot&#8221; for those who are just scraping the web, looking for forms to easily submit. You can add a textfield to the form, give it a name value of `_gotcha`, and then hide it using CSS. If any value is entered in this field, the message will be silently ignored. At the same time, this field is hidden from humans so that they won't accidentally enter anything.

~~~html
<input type="text" name="_gotcha" style="display:none" />
~~~

What about adding additional fields or features? Head on over to <a href="http://formspree.io/" target="_blank">their website</a> to see everything they've got to offer. This probably sounds like I'm being paid to write this post, but I'm not. I'm just grateful that I found a simple, easy solution to fill my needs. Enjoy!