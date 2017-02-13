---
layout: post
title:  "Connecting to External Databases In Drupal 7"
date:   2016-09-13 07:10:00 -0400
categories: drupal development
comments: true
---
{% include ganalytics.html %}

Recently at work I was tasked with finding a way to connect our Drupal 7 intranet site to our client database in order to prepopulate form fields with client data which in turn makes it easier on the sales people. When it comes to sales people, it's always a double edged sword. On one edge it's more efficient and less error prone to automate what they do, because the nature of how they work is very error prone. On the other edge however, it's just more spoon feeding that they can't seem to resist, and another excuse for them to not understand how things work because the system handles it for them. It also places the blame on us if something goes wrong.  

We all agreed this was a good idea, except nobody asked me what I thought. I wasn't familiar with connecting to external databases in Drupal, although I am the one who built and expanded our current Drupal site which is light years ahead of what we had with the old Sharepoint site. Sometimes it's good to just have a nudge in a certain direction, because I could always come back and tell them it's not feasible or would be way too complicated, if I needed to. Luckily, Drupal is very easy to work with and easy to customize.  

Add The Database
----------------

In **settings.php**, add the database credentials for the external database you'll be connecting to, something like this:
{% highlight php %}
<?php
 $databases = array (
   'default' =>
   array (
     'default' =>
     array (
       'database' => 'drupal_site',
       'username' => 'drupal_user',
       'password' => 'jfkd***',
       'host' => 'localhost',
       'port' => '',
       'driver' => 'mysql',
       'prefix' => '',
     ),
   ),

   'myexternaldatabase' =>
   array (
     'default' =>
     array (
       'database' => 'dbname',
       'username' => 'dbuser',
       'password' => 'dbpassword',
       'host' => 'db.url.local',
       'port' => '3306',
       'driver' => 'mysql',
       'prefix' => '',
     ),
   ),
 );
{% endhighlight %}

Write A Module
--------------

Write a custom module which connects to the database, does whatever it needs to, then reconnects to Drupal's database when it's done. In my case, I'm writing a simple module that will utilize [hook_form_alter][hookformalter]. Here's what mymodule.info looks like:
{% highlight conf %}
name = Prefill Webforms
description = whatever you want here
core = 7.x
dependencies[] = webform
{% endhighlight %}

And here's what mymodule.module looks like (so far):

{% highlight php %}
<?php

/**
 * @file
 * Pull data from the external database to prefill webforms.
 */

/**
 * Implements hook_help()
 *
 * Displays help and module information
 *
 * @param path
 *   Which path of the site we're using to display help
 * @param arg
 *  Array that holds the current path as returned from arg() function
 */
function prefill_webforms_help($path, $arg) {
  $output = '';

  switch ($path) {
    case "admin/help#prefill_webforms":
      $output = t('To use this module, create a webform, then modify the code of this module to handle that particular form upon submission.');
      break;
  }

  return $output;
}

/**
 * Implements hook_form_alter()
 *
 * @param form
 *   Nested array of form elements that comprise the form.
 * @param form_state
 *   A keyed array containing the current state of the form. The arguments that drupal_get_form() was originally called with are available in the array $form_state['build_info']['args'].
 * @param form_id
 *   String representing the name of the form itself. Typically this is the name of the function that generated the form.
 */
function prefill_webforms_form_alter(&$form, &$form_state, $form_id) {
  //dpm($form);
  if ($form_id == 'webform_client_form_229') {
    $form['#validate'][] = 'prefill_webforms_submit_handler';
  }
}

/**
 * Implements hook_submit_handler()
 *
 * @param form
 *   Nested array of form elements that comprise the form.
 * @param form_state
 *   A keyed array containing the current state of the form. The arguments that drupal_get_form() was originally called with are available in the array $form_state['build_info']['args'].
 */
function prefill_webforms_submit_handler($form, &$form_state) {
  // get submitted client ID from form
  $submitted_client_id = $form_state['input']['submitted']['client_id'];

  // select the maveric database defined in settings.php
  db_set_active('myexternaldatabase');
  // fetch the query using the submitted client ID
  $result = db_query("SELECT t.name, t.website FROM tablename t WHERE client_id = :client_id", arrary('client_id'=>$submitted_client_id));
  // set database connection back to default
  db_set_active();

  foreach($result as $record) {
    $form_state['values']['submitted']['client_name'] = $record->name;
    $form_state['values']['submitted']['website'] = $record->website;
  }

  //dpm($form);
  //dpm($form_state);
}
{% endhighlight %}

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

[hookformalter]: https://api.drupal.org/api/drupal/modules%21system%21system.api.php/function/hook_form_alter/7.x
