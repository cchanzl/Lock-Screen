---
layout: post
title: "PDF Scraping MAS Form 6"
category: python
date: 2020-06-05
---

Following from the initial lightweight exercise of <a href="https://cchanzl.github.io/python/2020/06/02/PDF-Scraping-MAS-Form-23"> obtaining Capital Adequacy Ratios </a> of insurers in the Singpaore market, i would go one step further to employ a similar technique in scraping the complete table in  MAS Form 6 - Statements of Premiums, Claims and Underwriting Results for SIF.

The process is largely similar from the previous exercise, except that it is more involved as we are no longer extracting a single number that is clearly identifiable by a symbol ("%"). Follow the comments in the code relating to each step below.

<b> # Extract raw text file of relevant pages </b>
<br>
This part of the code is where the PDFplumber module is required, to convert the relevant sections to text. First, we need to identify where Form 6 resides. Due to changes in formatting over the years, Form 6 - SIF can be split into two separate pages. Hence, the page_end identifier is where a page contains both "FORM 6" and "Overseas Insurance Fund", which is the page after SIF Form 6.

<b> # Extract values from Form 6 </b>
<br>
Once we have the relevant section as text produced as temp.txt, we can see that where values are extracted, they are often extracted as a single line after "Row No.". The unique identifier used to locate the start of the line of values is then (" " + str(row_number[i]) + " ") or (row_number[i]) + " "), where the latter is to account for Row No. starting at index 0.

However, this poses a challenge in cases where formulas in the form such as (10 + 11 - 12) triggers the IF statement as well. This is resolved by using another condition, relying on the apperance of ")". While this will create dupliates for longer formulas such as (13 - 26 - 27 - 30 - 31), we will deal with duplicate using Pandas df methods later.

<b> # Cleaning up </b>
<br>
With the right section and values extracted, we then proceed to clean up the file for lines starting with formulas. While lines with values are correctly extracted, the start of the line may contain some formulas as mentioned form the previous section. This part of the code is to remove any additional prefixes to our data and to add delimiters.

<b> # Creating Pandas df structure </b>
<br>
Pandas is again used to create dataframe to which we can add descriptive rows and column headers. These are saved in another text file. We also take the opportunity here to apply simple verifiation checks to ensure that the data is correctly cleansed and nothing escapes form the previous steps.

An important step here is to convert the str in df to int, particularly where some Forms display negative used "()" while others use "-". Hence, df.replace() is used to find and replace all "()" to be "-" which allows easy conversion to int.

<b> # Validation </b>
<br>
The last part if to then conduct a quick check that sum of certain rows in a column equals another row extracted. For now, this check is only performed on underwriting results. This validation check can be extended to other rows and to the column total as well.

<b> Final Output </b>
<br>
You can see from the picture below that the output at the end of the process is a clearly delimited text file. We can then build up a sizeable database upon which interesting visualisation and insights can be obtained by iterating this across multiple insurers and reporting years. I will leave this analysis for another post in the future, ending here with a quick insight gained from the historical Form 6 of an insurer A where we can clearly see a spike in Net Loss Ratio (NWP/Net Claims Settled) in 2015. We can also see that the 3 largest book in Insurer's A portfolio are Motor, Health and WIC by looking at how Total NLR trends historically.

<center> {% include line_NLR.html %} </center>

<img src="/images/Form6.PNG" style="width: auto; height: auto;max-width: 500px;max-height: 500px" class="center">
<p style="text-align:center">Sample output</p>


<script src="https://gist.github.com/cchanzl/30517ae13584c9ab5d1d558cde4e50ee.js"></script>
