---
layout: page
title: "Website Insights"
author: Rahul Pande
date: 2017-11-10 9:26:10 +0530
last_update: 2017-11-29 9:26:10 +0530
permalink: /projects/website_insights
---

# Website Insights

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

![website_screen_1]

The nodes are colored according to part of speech category, their sizes according to the occurrence frequencies. The links between nodes are gradient coloured according to the co-occurrence frequencies.

With this information, you can figure out what topics are being discussed in a website and what are the common context in which the topics are being discussed and also the sentiment surrounding it.

![website_screen_3]

[website_screen_1]: https://raw.githubusercontent.com/rahul-pande/website_insights/master/_screenshots/knowledge_graph.png
[website_screen_3]: https://raw.githubusercontent.com/rahul-pande/website_insights/master/_screenshots/graph_subset_2.png

