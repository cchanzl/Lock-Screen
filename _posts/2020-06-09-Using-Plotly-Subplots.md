---
layout: post
title: "Using Plotly Subplots"
category: python
date: 2020-06-09
---

In this post, i would leverage on the data scrapped from MAS Form 6 and utilise Plotly's subplots to show key metrics by lines of business for two local insurers - AXA and NTUC Income. Both companies are huge Motor insurance players in the market and it is interesting to see how their business volumes have decreased in recent years simultanesouly, although NTUC Income was able to maintain underwriting profitability while AXA suffered a loss in 2017. Both companies have also built up a sizeable motor claims reserve between 2008 and 2012 which then saw huge releases from 2013 onwards.

For a more complete and interactive dashboard, please refer to <a href="https://cchanzl.github.io/form%206/">MAS Form 6 Dashboard </a>in the directory above which is built using Dash and deployed using Heroku.

<center> {% include 6_dashboard_AXA.html %} </center>
<center> {% include 6_dashboard_NTUC.html %} </center>

<script src="https://gist.github.com/cchanzl/d2784389a731153c75c94bc01bd8c7fe.js"></script>
