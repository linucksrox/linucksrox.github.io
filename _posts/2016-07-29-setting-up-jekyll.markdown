---
layout: post
title:  "How To Get Going With Jekyll and GitHub Pages"
date:   2016-07-29 16:55:43 -0400
categories: jekyll install
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

[xubuntu]: http://xubuntu.org/
[github-pages-versions]: https://pages.github.com/versions/
