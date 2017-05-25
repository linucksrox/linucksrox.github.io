---
layout: post
title:  "SQLite, Content Providers, Cursor Adapters, and Cursor Loaders in Android"
date:   2017-05-25 07:30:00 -0400
categories: android development
comments: true
---
Android provides an **easy** way to connect to SQLite databases. It's so easy!!! But if you need to do anything beyond the most basic, single table, low record count database you might realize there's a little more to it. Welcome to [ContentProviders](https://developer.android.com/guide/topics/providers/content-providers.html), [CursorLoaders](https://developer.android.com/reference/android/content/CursorLoader.html), and [CursorAdapters](https://developer.android.com/reference/android/widget/CursorAdapter.html).

In this post (this might end up being a two part series, let's see), I want to dive into how all these things work together, explore some alternatives, and go into some specific examples while keeping it relatively simple. I want this to be an overview of the concepts that can be referenced later on.

Getting Started With SQLite
---------------------------

In **settings.php**, add the database credentials for the external database you'll be connecting to, something like this:
{% highlight java %}
public static final int PRODUCT = 4;
{% endhighlight %}


Write A Module
--------------
