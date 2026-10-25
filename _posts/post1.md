---
layout: post
title: analyzing malware retrieved from my Cowrie honeypot, and exploiting their mistakes
subtitle: found some weird stuff..
#cover-img: /assets/img/path.jpg
#thumbnail-img: /assets/img/thumb.png
#share-img: /assets/img/path.jpg
tags: [reverse engineering, honeypot]
---

hi, welcome to my first post.
today i'm writing up about my SSH honeypot with Cowrie. I recently bought a cheap vps from a local provider and i'm running multiple 'honeypot' services on it.

i have retrieved multiple files sent via SFTP, most of them are just random bash stuff, but there are 2 executables. today we are looking at one of them.

i sent the file over to my pc to have a better look at it, and had a look in detect it easy.

![die](https://i.imgur.com/NGgu6yk.png)

hmm, a go executable, how bad can it be?

i proceeded to open it in IDA, and had a look there

![ida1](https://i.imgur.com/SnlRO4T.jpeg)

![gopage](https://i.imgur.com/5dOzzNI.jpeg)

hmm, "golang.org/crypto/ssh". seems like one of the features of this executable is a custom TTY shell.

had a look at a random function within the list:

![ida2](https://i.imgur.com/cG4jFNV.jpeg)

![ida3](https://i.imgur.com/NYxz235.jpeg)

hm. definitely a TTY shell. lets look further

eventually, i found this and it caught my eye:

![ida4](https://i.imgur.com/cct4cI2.jpeg)

a whole bunch of functions, just double clicked on one, and there are the function names:

![ida5](https://i.imgur.com/jVXkUkF.jpeg)

yeah. definetely some sketchy shit alright.

we can see "anti task manager", "anti kill" (kill pid), other BS, and something mentioning XMR. at this point, i was sure it was a miner.

i looked up the hash on virus total,

![vt](https://i.imgur.com/vNwsfSy.png)

"discord-exploit". could we maybe find something relating to a webhook or bot?

i ran **strings /srv/honeypot-files/hash | grep -iE "webhook"**

![webhook](https://i.imgur.com/6SprBVZ.png)

holy shit there it is.

ran it via curl, sadly a 404, so the webhook isnt active anymore.

nevertheless, i thought this was fun to write about, and maybe educational for some.

thats how i found a webhook token from a simple go xmr miner uploaded on my honeypot. thanks for reading :)