---
layout: post
title:  "How To Get Going With Jekyll and GitHub Pages"
date:   2016-07-29 16:55:43 -0400
categories: jekyll install
comments: true
---
I'm running [Xubuntu 16.04][xubuntu]. This method should be the same/similar in any Debian/Ubuntu distro. These are the steps I followed to get this thing working, using the terminal. Note the Jekyll version, right now the latest version doesn't work with GitHub pages so I had to use a slightly older version (see the [GitHub dependency versions][github-pages-versions] page):
{% highlight bash %}
sudo apt install ruby ruby-dev ri bundler build-essential git
sudo gem install jekyll -v 3.1.6
sudo gem install minima
{% endhighlight %}

Next, you need to create a special repo in GitHub for your site. In GitHub, create a new repo, and name it:
{% highlight html %}
whatever-your-username-is.github.io
{% endhighlight %}

Finally, grab a local copy of the new repo:
{% highlight bash %}
git clone https://github.com/whatever-your-username-is/whatever-your-username-is.github.io
{% endhighlight %}

Create a brand new Jekyll site with the same name:
{% highlight bash %}
jekyll new whatever-your-username-is.github.io
{% endhighlight %}

Move to the directory:
{% highlight bash %}
cd whatever-your-username-is.github.io
{% endhighlight %}

Test your site locally by running this command, then go to the site it shows you in the terminal (default http://127.0.0.1:4000):
{% highlight bash %}
jekyll serve
{% endhighlight %}

Once you know it's working, or after you make whatever changes you want, throw it back up on GitHub!
{% highlight bash %}
git push
{% endhighlight %}

After you successfully push your newly created Jekyll site to GitHub, wait maybe 2-3 seconds (not really, it's just amazingly fast) and then go to:
{% highlight html %}
http://whatever-your-username-is.github.io
{% endhighlight %}

Start blogging!

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

[xubuntu]: http://xubuntu.org/
[github-pages-versions]: https://pages.github.com/versions/