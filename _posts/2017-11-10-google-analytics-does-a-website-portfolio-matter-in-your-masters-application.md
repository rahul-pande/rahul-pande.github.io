---
layout: post
title: "Google Analytics: Know when admission committees look at your website portfolio"
author: Rahul Pande
date: 2017-11-10 9:26:10 +0530
last_update: 2017-11-10 9:26:10 +0530
categories: analytics ga
---

How important is it to include a website portfolio in your master's application? Despite the availability of a lot of website solutions out of the box, publishing a website still takes up a significant amount of time. Is it worth it to spend that time on deploying a website when you could instead allocate that chunk of time in other aspects of the application, maybe improve your personal statement?

- [Do admission committees go through your website portfolio?](#do-admission-committees-go-through-your-website-portfolio)
- [Adding Google Analytics to your website](#adding-google-analytics-to-your-website)

### Do admission committees go through your website portfolio?

However, the second and more important question is- Do the admission committees visit your website when you put a link inline the essay? I never got a concrete answer to this question. So I decided to make a simple project out of it, with Google Analytics.

### Adding Google Analytics to your website

Sign up with [Google Analytics](https://analytics.google.com) and enter your website details. Under the **Admin** menu, in the **Property** sub-category, click on **Tracking Info**. Paste this tracking code in all of the pages that you want to be tracked. If you're using a template engine, make sure you include it in the head.

### Adding custom dimensions for event level tracking

GA does not allow exporting event level raw data. It only gives aggregated metrics. However there's an easy workaround for this. GA allows to introduce upto 20 custom dimensions. We can exploit this to add a user identifier ( set a bowser cookie) and a time field. So that if you were to query using the [**Query Explorer**](https://ga-dev-tools.appspot.com/query-explorer/) you would get event level data.

<details markdown="1">
<summary>Expand Tracking Code</summary>
~~~
<!--Google Analytics -->

<!-- Helper functions for cookies -->
<script>
  function createCookie(name,value,days) {
    if (days) {
      var date = new Date();
      date.setTime(date.getTime()+(days*24*60*60*1000));
      var expires = "; expires="+date.toGMTString();
    }
    else var expires = "";
    document.cookie = name+"="+value+expires+"; path=/";
  }

  function readCookie(name) {
    var nameEQ = name + "=";
    var ca = document.cookie.split(';');
    for(var i=0;i < ca.length;i++) {
      var c = ca[i];
      while (c.charAt(0)==' ') c = c.substring(1,c.length);
      if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
    }
    return null;
  }

  function eraseCookie(name) {
    createCookie(name,"",-1);
  }

  function uuidv4(){
    return ([1e7]+-1e3+-4e3+-8e3+-1e11).replace(/[018]/g, c =>
      (c ^ crypto.getRandomValues(new Uint8Array(1))[0] & 15 >> c / 4).toString(16)
      )
  }
</script>


<!-- analytics.js -->
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  var cookieName = 'browser_uuid'

  if(readCookie(cookieName) == null){
    createCookie(cookieName, uuidv4(), 365)
  }

  ga('create', '{GA_tracking_code}', 'auto');

  /* Assign a cookie to browser_id custom dimension */
  ga('set', 'dimension1', readCookie(cookieName));

  /* Assign millisec to utc_millisec custom dimension */
  ga('set', 'dimension2', new Date().getTime());

  ga('send', 'pageview');

</script>
~~~
{: .language-html}
</details>

<br>

![](/assets/img/custom_ga_dimension.png)

### Setting up Custom Campaigns

If your website already has significant traffic from the places that you're Universities are, you would need to set up custom campaigns to distinguish the application statement traffic from the other traffic. You can use the [Campaign URL Builder](https://ga-dev-tools.appspot.com/campaign-url-builder/) and setup up links for different Universities that you're applying to.

![](/assets/img/custom_ga_campaign.png)


// In progress. Please check back again.
