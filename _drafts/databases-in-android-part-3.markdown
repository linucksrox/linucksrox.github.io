---
layout: post
title: 'Databases In Android - Part 3'
date: '2017-06-16 06:59'
categories: android development
comments: true
---

ContentProviders
----------------

Let's get right into it. [ContentProviders](https://developer.android.com/guide/topics/providers/content-providers.html) manage access to data, and provide a layer of abstraction between raw data and the application (widget, other apps, your own app, etc.). At the expense of a little more complexity, it adds the value of centralized data security (instead of making outside applications sanitize data, it can all be done in the provider). You can also change the data backend without making any changes to the provider API, and so no changes are necessary in any applications accessing the provider. For example you could change from using a flat file data store to using a SQLite database.
