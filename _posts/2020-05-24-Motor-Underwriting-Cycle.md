---
layout: post
title: "Motor Underwriting Cycle"
category: Tableau
date: 2020-05-25
---

In this post, i would use historical data from Singapore's motor insurace market to showcase the underwriting cycle experienced between 2005 to 2014. The data source supporting this visualisation is from the Monetary Authority of Singapore, based on their collection of annual insurance returns of insurers in the local market. I would make another post on how to efficiently extract information from these insurance returns using Python.

As we run through each financial year from 2005 onwards using the scroll bar below, we can see from the bottom graph that the market overall combined ratio increases to a peak of 121% in 2008 before decreasing to 86% in 2014. It is clear from this that the market had seen a full underwriting cycle between 2005 to 2014 (a period of ten years).

Looking at the top graph, we can focus on individual insurers and their respective performance during the same period. Insurers within the market made a rightward shift towards a high combined ratio position from 2005 to 2008 before reverting to a low combined ratio position post 2005. While this is not surprising given the overall market trend already established above, what is interesting is the general "ɔ" shape movement. This movement showcases the reduction in market share as combined ratio improves.

Isolating AIG for example, we can see that it started off in 2005 with a Motor combined ratio of 90% and a Motor market share of 24%. This changed to a combined ratio of 123% and a Motor market share of 26% by 2007. By 2014, their market share was 16%, with a combined ratio of 98%.

Adding in a time dimension to the graph allows us to further understand which insurer reacted fastest and strongest to market trends. For example, Tokio Marine Insuranc's combined ratio improved a whooping 148% to 111% from 2008 to 2009 which is above market movement in the same year. Between 2008 and 2009 was also when we observed every major market player making some sort of strategic adjustment, resulting in significant improvement across individual performance.

<iframe src="https://public.tableau.com/shared/T5R4BT6RP?:showVizHome=no&:embed=true" width="900" height="2000" frameborder="true"></iframe>
Note that the visualisation only contains performance for the top ten motor insurers during the period.



