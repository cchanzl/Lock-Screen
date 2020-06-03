---
layout: post
title: "PDF Scraping using PDFminer3"
category: python
date: 2020-06-02
---

The first step in preparing good data visualisation is having good data. Data come from many sources including both internally within the company as well as externally such as those publicly available from regulators. This post would focus on the latter, where i would showcase a proof of concept by using Python to scrap useful information from the annual MAS insurer returns. This is done via the PDFminer3 module.

The annual MAS insurer returns is selected because of the amount of useful information contained within, specific to individual insurers but yet it remains highly inaccessible due to its file type as a PDF. As a start, i would focus on Form 23, which contains the Capital Adequacy Ratio ("CAR") of the insurer. The reason for this is because the CAR is easily identifiable with "%" hence making it easily recognisable once i zoom into the right portion of the PDF. 

I would explore other parts of the returns such as Form 6 where it would not be trivial in identifying and allocating values to the various columns. The source code for this scraping exercise is below, accompanied by a line graph comparing the historical CAR position of selected insurers in the market.

A potential future improvement would be to optimise the code such that it runs faster for longer reporting years and insurers. With this, a future use case would be to automate the production of a dashboard for an insurer's single year of return, showcasing key financial information.


<center> {% include Line.html %} </center>

<script src="https://gist.github.com/cchanzl/b0627c144130fa4d711c7faa6227ea63.js"></script>

<script src="https://gist.github.com/cchanzl/0001289708c3ebfa9a7f235759670195.js"></script>
