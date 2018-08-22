---
layout: single
author_profile: true
---

There's not enough time to learn everything I want to know. At the same time most of my knowledge is not documented, so this blog exists for me to share my knowledge and help people understand things that I've already learned through experience.

Highlights of My Experience
===

Software Development
---
Currently I'm focused on learning Android development in my free time. I've spent the most time learning and playing with C++ and Java, so Android is a natural progression of those skills. I'm writing all new code in Kotlin starting with chapter 24 (Nerd Launcher). These are two of my projects that I think are particularly cool:
- [Textecutor](https://github.com/linucksrox/Textecutor) - Send a text message to someone you need to call, turning their ringer to full max volume (they just need the app installed and your phone number needs to be on their authorized list of people). This is a work in progress, but is usable in its current state.
- [Lights Out](https://github.com/linucksrox/AndroidLogicPuzzle) - This is just a clone of the classic Tiger Electronics handheld game where you have to turn off all the lights. I'm particularly interested in creating an algorithm which can calculate the fewest number of possible moves to solve.

System Administration
---
I manage two physical servers at home: FreeNAS for storing files over my network, and ESXi running about 10 VMs for various services. Currently I'm learning Docker and looking at building docker-compose files to "dockerize" my production apps and restructure my setup for more efficiency and ease of updates/deployment later on (like if I need to rebuild my entire setup from a backup).
- pfSense firewall
- bind DNS
- Nextcloud using FreeNAS as the backend storage, supporting 6 users. Combine this with the Nextcloud app, and you have a nice picture backup system for free!
- Ampache music streaming server (using dsub on Android for a Pandora like experience with my personal music collection)
- a random Linux distro using the lightweight LXDE which primarily runs Crashplan for backing up most data on my FreeNAS
- Nginx reverse proxy - this sits in front of Nextcloud and Ampache
- OpenVPN for external access into my network and security on public Wi-Fi networks
- Wazo PBX combined with Voip.ms service, allowing me to use my phone as a SIP extension and make outgoing calls from my house. Without this it's difficult to make calls without going outside.
- Prosody as a chat server using the XMPP protocol (paired with Conversations for Android). This is far more reliable than SMS and especially MMS.

Music
---
Aside from programming and other technology interests, I play the piano (lately I'm mostly using my Yamaha KX8 controller with Waves Grand Rhapsody Red Piano preset) and really enjoy recording music. [Check out some piano music I've written on SoundCloud.](https://soundcloud.com/linucksrox)
