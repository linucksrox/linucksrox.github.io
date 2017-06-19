---
layout: post
title: Databases In Android - Part 3
date: '2017-06-19 06:45'
categories: android development
comments: true
---

Before I get into ContentProviders, I just want to mention how difficult it is to blog consistently. I mean, it's not too bad. You just have to commit to a schedule and stick with it. You just have to be motivated to write instead of work on your app that is probably way more interesting to work on. It's not a complaint though, more of a rant. There's just not much time available to work on side projects when you have a full time job and family to spend time with, assuming you don't work for Apple.

<br>
![](/assets/images/apple-rarely-get-to-see-my-kids.jpg)
<br>
<br>
That's not me. It's the other way around:
> I have to limit how much I work, or I risk not seeing my kids.

<br>

ContentProviders
----------------

[ContentProviders](https://developer.android.com/guide/topics/providers/content-providers.html) manage access to data, and provide a layer of abstraction between raw data and the application (widget, other apps, your own app, etc.). At the expense of a little more complexity, it adds the value of centralized data security (instead of making outside applications sanitize data, it can all be done in the provider). You can also change the data backend without making any changes to the provider API, and so no changes are necessary in any applications accessing the provider. For example you could change from using a flat file data store to using a SQLite database.

<br>
<br>
Well I ran out of time today, so I'll add to this next time.

{% if page.comments %}
<div id="disqus_thread"></div>
<script>
    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables
     */
    /*
    var disqus_config = function () {
        this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    */
    (function() {  // DON'T EDIT BELOW THIS LINE
        var d = document, s = d.createElement('script');
        
        s.src = '//blog-dalydays-com.disqus.com/embed.js';
        
        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
{% endif %}
