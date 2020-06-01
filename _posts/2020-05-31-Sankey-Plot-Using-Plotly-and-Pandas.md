---
layout: post
title: "Sankey Plot Using Plotly and Pandas"
category: python
date: 2020-05-31
---

In this post, i would visualise the change and breakdown of monthly expenses since i moved to London using Plotly, Python's visualisation library. The source code for this visualisation is included in the gist below. There are significant improvements to be made in the way data is treated and subsequently used in order to derive the plot.

One of these improvements which have been implements is the use of a dataframe from the Pandas library, enabling more efficient and easier access to underlying values. Also, the colours and labels of the trace can be further refined to provide better information and visual cues.

However, the current diagram does serve its purpose. For example, we can see a clear reduction in expenses incurred from eating out between September and May, which is clearly due to Covid-19. A corresponding increase in amount spent on groceries is seen in the same period.

In summary, this plot is a good start to understanding the vast library of traces offered by Plotly and the level of customisation possible which i am keen to explore further.

<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>

<center> {% include Sankey.html %} </center>

<script src="https://gist.github.com/cchanzl/6b3b584633e47cd40541aaaa332d9d60.js"></script>
