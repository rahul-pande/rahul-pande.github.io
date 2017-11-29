---
layout: post
title: "Google Analytics: Know when admission committees look at your website portfolio"
author: Rahul Pande
date: 2017-11-10 9:26:10 +0530
last_update: 2017-11-10 9:26:10 +0530
categories: analytics ga
---

How important is it to include a website portfolio in your master's application? Despite the availability of a lot of website solutions out of the box, publishing a website still takes up a telling amount of time. Is it worth it to spend that time on deploying a website when you could instead allocate that chunk of time in other aspects of the application, maybe improve your personal statement?

- [Do admission committees go through your website portfolio?](#do-admission-committees-go-through-your-website-portfolio)
- [Adding Googla Analytics to your website](#adding-google-analytics-to-your-website)

## Do admission committees go through your website portfolio?

However, the second and more important question is- Do the admission committees visit your website when you put a link inline the essay? I never got a concrete answer to this question. So I decided to make a simple project out of it, with Google Analytics.

## Adding Google Analytics to your website

Sign up with [Google Analytics](https://analytics.google.com) and enter your website details. Under the **Admin** menu, in the **Property** sub-category, click on **Tracking Info**. Paste this tracking code in all of the pages that you want to be tracked. If you're using a template engine, make sure you include it in the head.

## Adding custom dimensions for event level tracking

GA does not allow exporting event level raw data. It only gives aggregated metrics. However there's an easy workaround for this. GA allows to introduce upto 20 custom dimensions. We can exploit this to add a user identifier ( set a bowser cookie) and a time field. So that if you were to query using the Core Reporting API(https://ga-dev-tools.appspot.com/query-explorer/) you would get event level data.

## Setting up Custom Campaigns

If your website already has significant traffic from the places that you're Universities are, you would need to set up custom campaigns to distinguish the application statement traffic from the other traffic.

// In progress. Please check back again.
