---
layout: post
title: "Setting up Python Dashboard"
category: python
date: 2020-06-19
---

Setting up and hosting a dashboard online as i did for MAS Form 6 may look daunting at first. However, the steps required are relatively straightforward and a fair bit of patience!

<b> Initial Setup </b>
<br>

Before I jump into the steps, we would need the following installed. If you have been exploring Python and Plotly, some of these basic requirements would have already been fulfilled. Note that these does not include the required Python packages which you can find out under "requirements.txt" in a subsequent step or see in the source code.
<ol>
  <li>
    Pycharm
  </li>
  
  <li>
    Git Bash (required for pushing updates to Heroku)
  </li> 
</ol>
There are other requirements (such as Git Bash and a Heroku account) but we will get to these as we go through each step.

<b> Step 1: Deploy a sample dashboard </b>
<br>

Before you put in hours setting up your visualisations, we need to ensure that you are able to set up your machine to deploy them. Afterall, there is not really any point preparing visualisations for an audience of one. To do this, you need to follow <a href="https://dash.plotly.com/deployment"> this guide. </a> I would not repeat the steps in the guide as they are fairly straightforward. However, i would touch on my experience, having been through it.

The first few steps up to step 2 should not take too long. I had some difficulty with creating a virtual environment as the path was not found. But a quick google search did the trick.

For step 3, you need to be careful when creating Procfile. As highlighted in <a href="https://devcenter.heroku.com/articles/procfile"> Heroku's documentation </a>, the Procfile is always a simple text file that is named Procfile without a file extension. For example, Procfile.txt is not valid. I made the simple mistake of creating a text file and simply naming it as required. If you are having difficulty, feel free to take a copy of the Procfile i used from my repo.

Another misstep i made was when creating "requirements.txt". This can be created easily through the Python terminal in Pycharm. What you need to remember is to update this file when you add packages in your source code, especially when you update your dashboard with new graphs.

By the end of this step, you would have created a free Heroku account and am able to now view/embed the sample dashboard on your site.
