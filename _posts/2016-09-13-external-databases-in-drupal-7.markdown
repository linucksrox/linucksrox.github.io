---
layout: post
title:  "Connecting to External Databases In Drupal 7"
date:   2016-09-13 07:10:00 -0400
categories: drupal development
comments: true
---
[Udacity][udacity]{:target="_blank"}  

Intro
=====
Recently at work I was tasked with finding a way to connect our Drupal 7 intranet site to our client database in order to prepopulate form fields with client data which in turn makes it easier on the sales people. When it comes to sales people, it's always a double edged sword. On one edge it's more efficient and less error prone to automate what they do, because the nature of how they work is very error prone. On the other edge however, it's just more spoon feeding that they can't seem to resist, and another excuse for them to not understand how things work because the system handles it for them. It also places the blame on us if something goes wrong.  

We all agreed this was a good idea, except nobody asked me what I thought. I wasn't familiar with connecting to external databases in Drupal, although I am the one who built and expanded our current Drupal site which is light years ahead of what we had with the old Sharepoint site. Sometimes it's good to just have a nudge in a certain direction, because I could always come back and tell them it's not feasible or would be way too complicated, if I needed to. Luckily, Drupal is very easy to work with and easy to customize.  

So How Do You Do It?
====================
There are a couple things:

* In **settings.php**, add the database credentials for the external database you'll be connecting to, something like this:
{% highlight php %}
$databases = array();
$databases['default']['default'] = array(
  // Drupal's default credentials here.
  // This is where the Drupal core will store its data.
);
$databases['my_other_db']['default'] = array(
  // Your external database - copy drupal's credentials above,
  // then substitute your database credentials here.
);
{% endhighlight %}

* Write a custom module which connects to the database, does whatever it needs to, then reconnects to Drupal's database when it's done.

<br />
<br />
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

[udacity]: https://www.udacity.com/