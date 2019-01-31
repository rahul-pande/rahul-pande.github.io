---
layout: post
title: "Google Analytics: Know when admission committees look at your website portfolio"
author: Rahul Pande
date: 2017-11-10 9:26:10 +0530
last_update: 2017-11-29 9:26:10 +0530
categories: analytics ga
---

How important is it to include a website portfolio in your master's application? Despite the availability of a lot of website solutions out of the box, publishing a website still takes up a significant amount of time. Is it worth it to spend that time on deploying a website when you could instead allocate that chunk of time in other aspects of the application, maybe improve your personal statement?

## Contents

- [Do admission committees go through your website portfolio?](#do-admission-committees-go-through-your-website-portfolio)
- [Adding Google Analytics to your website](#adding-google-analytics-to-your-website)
- [Adding custom dimensions for event level tracking](#adding-custom-dimensions-for-event-level-tracking)
- [Setting up Custom Campaigns](#setting-up-custom-campaigns)
- [Analytics](#analytics)

### Do admission committees go through your website portfolio?

However, the second and more important question is- Do the admission committees visit your website when you put a link in the essay? I never got a concrete answer to this question. So I decided to make a simple project out of it, with Google Analytics.

### Adding Google Analytics to your website

Sign up with [**Google Analytics**](https://analytics.google.com){: target='_blank'} and enter your website details. Under the **Admin** menu, in the **Property** sub-category, click on **Tracking Info**. Paste this tracking code in all of the pages that you want to be tracked. If you're using a template engine, make sure you include it in the head.

### Adding custom dimensions for event level tracking

GA does not allow exporting event level raw data. It only gives aggregated metrics. However, there's an easy workaround for this. GA allows up to 20 custom dimensions. We can exploit this to add a user identifier ( set a browser cookie) and a time field. So that if you were to query using the [**Query Explorer**](https://ga-dev-tools.appspot.com/query-explorer/){: target='_blank'} you would get event-level data.

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

If your website already has significant traffic from the places that you're Universities are, you would need to set up custom campaigns to distinguish the application statement traffic from the other traffic. You can use the [**Campaign URL Builder**](https://ga-dev-tools.appspot.com/campaign-url-builder/){: target='_blank'} and setup up links for different Universities that you're applying to.

**Important Note:**
> Inserting a shortened URL in a University application is not a good idea since you don't have user's consent to be tracked.
> This is why I think you should refrain from using URL shortening services like bit.ly.
> Instead, enter plan website name like rahulpande.me and then link it to the custom tracking URL; that way the user could still copy paste the text if he wishes to be not tracked explicitly


![](/assets/img/custom_ga_campaign.png)

You should have something like below in your Query Explorer Result which you can export as CSV.

![](/assets/img/ga_raw_data.png)

### Analytics
You could do a whole bunch of analytics around this. Some points that I will be publishing at the end of this exercise are:
- Do Universities look beyond the main landing page?
- Comparing time spent on different posts and pages
- It would also be interesting to see the box plot of the number of website visits versus University application outcome (admit/reject) and then check how much of the variation in the number of visits can be explained by the University outcome.

If you have any thoughts on this, please let me know in the comments section!
