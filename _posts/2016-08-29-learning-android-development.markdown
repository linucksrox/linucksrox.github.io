---
layout: post
title:  "My Android Development Journey"
date:   2016-08-29 06:55:43 -0400
categories: android development
comments: true
---
{% include ganalytics.html %}

Lately I've been learning to develop for Android using [Udacity][udacity]{:target="_blank"}. There are a lot of other good resources available, but Udacity seems promising because the Android courses were developed by Google and Udacity.

I wouldn't consider myself a beginner in programming, but I also don't have a ton of work experience (maybe more than I realize though). I do some limited JavaScript at work to manipulate [BIRT][birt]{:target="_blank"} reports. I also wrote a company portal site using PHP which authenticates against our Active Directory server to log in. I excelled in C and C++ when I was learning that 10+ years ago by reading books and visiting the [CProgramming][cprogramming]{:target="_blank"} forums. In particular, [C Primer Plus][cprimerplusbook]{:target="_blank"}, and heck yes, I have the first edition. I found it for $1 at a Goodwill, and it is one of the best programming books I've read.

So lately I'm realizing more and more that my job value is not all about how much I already know. It's all about being able to learn what I need to know and being able to get something done. When I think back to any job I've ever had, that's how it worked. I didn't know everything before getting hired, I used some past experience and applied it to the new environment, adding new skills and knowledge along the way. I used to think I needed to "learn" a programming language which to me meant I needed to read books and make sure I could complete all the chapter exercises, and after I completed the "advanced" sections that I would be capable of programming in C (or whatever language). The reality is that I wasted tons of time memorizing how to do things like memory management in C (malloc), use pointers, and a bunch of other stuff I have never used outside of the practice problems. Sure it's valuable from an academic standpoint, but not from a career advancement standpoint. It's not about book learning, it's about experience. Learn primarily by doing and not primarily by reading. If you're going to read a book, do while you read. I'm realizing this now, and this is what I plan to do about it.

The best thing I can do is start programming things. I don't think I will come up with the best ideas for game changing apps that will change the world, but I can write apps that copy other ideas, just for practice. But that's practice that has real world value. Practice interacting with databases, practice authenticating users, and practice arranging layouts. The more I do now, the less time it will take me on the job.

At this point, I've decided to learn Android. I also realize I will never be an expert in one area, maybe not even Android. But I am an expert in learning what I need to know to move forward with a problem and get the job done. Right now I will focus on learning Android by going through the courses at Udacity and writing apps. I post everything I do to [GitHub][github]{:target="_blank"} for anyone to check out. I particularly enjoyed the MediaPlayer sample app which I used to play the Rick Roll song, then I disabled the Pause/Stop buttons and installed it on a friend's phone. It's hilarious because you can't stop the music without force closing the app. Don't worry, I won't publish that to the Play store.

I plan to learn Android, and I'm committing to writing a blog once a week, starting now. I want to mention John Sonmez at [Simple Programmer][simpleprogrammer]{:target="_blank"}. I saw him on Youtube first, and wasn't sure of my opinion. After reading his blog and watching more videos though, I agree with a lot of what he says and it just started to click. This is me taking action and starting my blog.

<a href="http://simpleprogrammer.com/2015/03/02/my-free-blogging-course-is-getting-unbelievable-results/"><img src="http://simpleprogrammer.com/wp-content/uploads/2015/04/badge.png"></a>

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
[birt]: http://www.eclipse.org/birt/
[cprogramming]: http://www.cprogramming.com/
[cprimerplusbook]: https://www.amazon.com/Groups-Primer-Mitchell-Stephen-Paperback/dp/B011DC2HNG?SubscriptionId=AKIAILSHYYTFIVPWUY6Q&tag=duckduckgo-d-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B011DC2HNG
[github]: https://github.com/linucksrox
[simpleprogrammer]: https://simpleprogrammer.com/
