---
layout: page
title: Projects
permalink: /projects/
---

### Android App for Vishwakarma Institute of Technology

<div class="list-group">
  <a class="list-group-item icon-link" href="https://github.com/rahul-pande/vit" target="_blank">
    <i class="fa fa-github fa-2x" title="Github Repo"></i>
  </a>
  <a class="list-group-item icon-link" href="https://play.google.com/store/apps/details?id=com.rahul7teen.vit" target="_blank">
    <i class="fa fa-android fa-2x" title="PlayStore"></i>
  </a>
</div>

**Features:**
* Simple UI
* Push Notifications for communication between the management and students
* Easy Download Section
* Light and Blazing Fast (900kB)

The app was built with Google Cloud Messaging, and served as a **notification medium** for important college events like semester registration deadline, flash mobs, etc. It was also a convinient option for students to **download** all types of important documents like class time tables, curriculum.

![vit_screen_1] ![vit_screen_2] ![vit_screen_3]

[vit_screen_1]: https://raw.githubusercontent.com/rahul-pande/vit/master/scr1.png
{:height="400" width="242"}
[vit_screen_2]: https://raw.githubusercontent.com/rahul-pande/vit/master/scr2.png
{:height="400" width="242"}
[vit_screen_3]: https://raw.githubusercontent.com/rahul-pande/vit/master/scr3.png
{:height="400" width="242"}

<br>

### Website Insights

<div class="list-group">
  <a class="list-group-item icon-link" href="https://github.com/rahul-pande/website_insights" target="_blank">
    <i class="fa fa-github fa-2x" title="PlayStore"></i>
  </a>
</div>

The project has four main components:
+ [**Scrapy**](https://scrapy.org/){:target="blank"} crawler to parse websites for data like posts and comments
+ [**NLTK**](http://www.nltk.org/){:target="blank"} processing pipeline to extract nouns and adjectives using POS (Part Of Speech) tagger
+ Aggregation in Python using [**Pandas**](https://github.com/pandas-dev/pandas){:target="blank"} to generate word frequencies and word co-occurences
+ [**D3**](https://d3js.org/){:target="blank"} force simulations to vizualize the co-occurences

![website_screen_3]

The nodes are colored according to part of speech category, their sizes according to the occurrence frequencies. The links between nodes are gradient coloured according to the co-occurrence frequencies.

With this information, you can figure out what topics are being discussed in a website and what are the common context in which the topics are being discussed and also the sentiment surrounding it.

![website_screen_1]

[website_screen_1]: https://raw.githubusercontent.com/rahul-pande/website_insights/master/_screenshots/knowledge_graph.png
[website_screen_3]: https://raw.githubusercontent.com/rahul-pande/website_insights/master/_screenshots/graph_subset_2.png
