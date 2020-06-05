---
layout: post
title: "PDF Scraping MAS Form 6"
category: python
date: 2020-06-05
---

Following from the initial lightweight exercise of <a href="https://cchanzl.github.io/python/2020/06/02/PDF-Scraping-MAS-Form-23"> obtaining CAR information </a> of insurers in the Singpaore market, i would go one step further to employ a similar technique in scraping the complete tabl in  MAS Form 6 - Statements of Premiums, Claims and Underwriting Results for SIF.

The process is largely similar from the previous exercise, except that it is more involved as we are no longer extracting a single number which is clearly identifiable by a symbol. I will update this post with the detailed steps soon but 

<b> # Extract raw text file of relevant pages </b>
<br>
To be updated...

<b> # Extract values from Form 6 </b>
<br>
To be updated...

<b> # Cleaning up </b>
<br>
To be updated...

<b> # Creating Pandas df </b>
<br>
To be updated...

<b> # Validation </b>
<br>
To be updated...

<b> Final Output </b>
<br>
You can see from the picture below that the output at the end of the process is a clearly delimited text file. We can then build up a sizeable database upon which interesting visualisation and insights can be obtained by iterating this across multiple insurers and reporting years. I will leave the analysis for another post in the future.

<img src="/images/Form6.PNG" style="width: auto; height: auto;max-width: 500px;max-height: 500px" class="center">
<p style="text-align:center">Sample output</p>

<script src="https://gist.github.com/cchanzl/30517ae13584c9ab5d1d558cde4e50ee.js"></script>
