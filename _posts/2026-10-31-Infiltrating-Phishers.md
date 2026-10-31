---
layout: post
title: Infiltrating malicious Telegram bots
subtitle: How crappy phishing sites can be exploited
#cover-img: /assets/img/path.jpg
#thumbnail-img: /assets/img/thumb.png
#share-img: /assets/img/path.jpg
tags: [phishing, telegram]
---

Gday,
Today I will be showing you how to infiltrate malicious Telegram bots linked to phishing sites.

These phishing sites are easily found on sites like PhishTank, or anything similar.
I noticed that most of these phishing sites with telegram bots are usually Facebook ones.
They are usually either a fake ban appeal, or a fake "verification checkmark" site.
Even though these types of sites look really crappy to me and you, tech-illiterate people don't know any better.
These types of sites are usually ran by Turkish or Vietnamese people, from what I've seen.

![1](https://i.imgur.com/xsk0LMR.jpeg)

This is an example of one of those "phishing toolkits".
To be honest, it looks really realistic and I can see someone falling for this.

After clicking on "Submit request", it shows you this:

![2](https://i.imgur.com/WPnrckq.jpeg)

When you put in this info, a request is made:

![3](https://i.imgur.com/l5ph4iP.jpeg)

This is what you want to see. You need a Chat ID, and the "bot token" to forward everything to you.

![4](https://i.imgur.com/C2SUlgu.jpeg)

And as you can see, it shows you the chat ID in the headers here including what it's sending.
From there, you can use a tool like [Matkap](https://github.com/0x6rss/matkap) to infiltrate the bot and make it send stuff to you.

I'm not going into Matkap and how it works too much, but it basically forwards everything in a chat (from the chat ID) to your telegram account.

To properly use Matkap, you need your own bot ID, and secret hash.

Eventually, I got it to forward a message.

The only message in that chat was my decoy, which means that I'm their first catch.
That's quite pathetic.

![5](https://i.imgur.com/n5icY1C.png)

But to show you that this actually does work, here's a bot that i intercepted about 2 weeks ago.
This one had over 3000 messages:

![6](https://i.imgur.com/rwCknMx.png)

Well, that was all I had in store for you.

Thank you for reading, have a good one. <3