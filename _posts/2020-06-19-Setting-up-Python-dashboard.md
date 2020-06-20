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

1. Pycharm
2. Git Bash (required for pushing updates to Heroku)

There are other requirements (such as Git Bash and a Heroku account) but we will get to these as we go through each step.

<b> Step 1: Deploy a sample dashboard </b>
<br>

Before you put in hours setting up your visualisations, we need to ensure that you are able to set up your machine to deploy them. Afterall, there is not really any point preparing visualisations for an audience of one. To do this, you need to follow <a href="https://dash.plotly.com/deployment"> this guide. </a> I would not repeat the steps in the guide as they are fairly straightforward. However, i would touch on my experience, having been through it.

The first few steps up to step 2 should not take too long. I had some difficulty with creating a virtual environment as the path was not found. But a quick google search did the trick.

For step 3, you need to be careful when creating Procfile. As highlighted in <a href="https://devcenter.heroku.com/articles/procfile"> Heroku's documentation </a>, the Procfile is always a simple text file that is named Procfile without a file extension. For example, `Procfile.txt` is not valid. I made the simple mistake of creating a text file and simply naming it as required. If you are having difficulty, feel free to take a copy of the Procfile i used from my repo.

Another misstep i made was when creating `requirements.txt`. This can be created easily through the Python terminal in Pycharm. What you need to remember is to update this file when you add packages in your source code, especially when you update your dashboard with new graphs.

By the end of this step, you would have created a free Heroku account and am able to now view/embed the sample dashboard on your site.

<b> Step 2: Customising the layout of your dashboard </b>
<br>

This step is where you prescribe a format for your dashboard. For this, I relied heavily on the steps <a href="https://www.statworx.com/at/blog/how-to-build-a-dashboard-in-python-plotly-dash-step-by-step-tutorial/"> in this tutorial. </a> Without changing the key portion of the code which enables deployment to Heroku and focussing the changes on `app.layout`, i was able to deploy the dashboard in this tutorial instead of the example in step 1.

The reason for this is that the source code for the dashboard in this tutorial is scalable. This lets me make subsequent changes suited to my preference. For example, i can now update the CSS such that the background of the dashboard is white and change the layout to be a single column (or really any other layout).

An important part of the code which will be used repeatedly would be `app.callback()`. This is where the integration with Plotly comes in for the next step.

```python
@app.callback(Output('nwp_bar', 'figure'),
              [Input('lobselector', 'value'), Input('insurerselector', 'value')])
def update_lossratio(lobselector, insurerselector):
```

<b> Step 3: Adding visualisations </b>
<br>

Visualisations is first referenced in the app.layout as seen in the code below. The keyword here is "id=". This is how html recognises which visualisation to place at which location in the dashboard. The same id would then be reference in `app.callback()` later in the code. That is also where we will customise our visualisation, including its type and styling.

Next, we can then create the visualisation. This is done in the code below. You would have the same block of code for every visualisation in the dashboard. Any graph in Plotly's library would work here and the syntax is the same so i would not elaborate further.

```python
@app.callback(Output('ranking_line', 'figure'),
              [Input('lobselector', 'value')])
def update_market_rank(lobselector):
    # STEP 1
    trace = []
    # STEP 2
    # Draw and append traces for each stock
    for lob in lobselector:
        df_rank = df2[['year', 'insurer_name', 'Description', lob]]
        df_rank = df_rank[df_rank.Description == 'GWP - Direct business']
        df_rank_final = pd.DataFrame(columns=['year', 'insurer_name', 'Description', lob, 'Market_Rank'])
        for y in years:
            df_rank_y = df_rank[df_rank.year == y]
            df_rank_y['Market_Rank'] = df_rank_y[lob].rank(method='max', ascending=False)
            df_rank_final = pd.concat([df_rank_final, df_rank_y])
        for i in unique:
            df_rank_final_i = df_rank_final[df_rank_final.insurer_name == i]
            trace.append(go.Scatter(x=df_rank_final_i['year'].tolist(),
                                    y=df_rank_final_i['Market_Rank'].tolist(),
                                    opacity=0.7,
                                    name=i + " - " + lob,
                                    legendgroup=i,
                                    marker_size=25,
                                    textposition='bottom center',
                                    text=df_rank_final_i['insurer_name'] + " - " + lob,
                                    hovertemplate=
                                    "<b>%{text}</b><br>" +
                                    "Year: %{x:.f}<br>" +
                                    "Rank: %{y:.s}<br>" +
                                    "<extra></extra>",
                                    ))
    # STEP 3
    traces = [trace]
    data = [val for sublist in traces for val in sublist]
    # STEP 4
    figure = {'data': data,
              'layout': go.Layout(
                  margin=dict(b=40, t=10),  # l, r, b, t
                  paper_bgcolor='rgba(0, 0, 0, 0)',
                  plot_bgcolor='rgba(0, 0, 0, 0)',
                  hovermode='closest',
                  showlegend=True,
                  height=600,
                  autosize=True,
                  yaxis=dict(
                      range=[0, len(unique) + 1],
                      autorange="reversed",
                      title='Market Ranking',
                      tickformat=".s",
                      titlefont=dict(
                          family='Arial',
                          size=15,
                          color='lightgrey')
                  ),
                  xaxis=dict(
                      title='Reporting Year',
                      titlefont=dict(
                          family='Arial',
                          size=15,
                          color='lightgrey')
                  ),
              ),
              }

    return figure
```

<b> Step 4: Debugging </b>
<br>

During the course of setting up the dashboard, you can debug it by tpying python app.py in Pycharm Python console. This is assuming oyu named your Python file `app.py`. This allows you to view the dashboard locally in your browser, without deploying to Heroku. I do this every so often so that i know which incremental change results in a bug.

<b> Step 5: Pushing to Heroku </b>
<br>

The last step when you are ready is to commit and push the dashboard to Heroku for deployment on your site. you would have already done this from Step 1 above.

<b> Conclusion </b>
<br>

It took me a day to set up the dashboard from scratch and possibly another two weeks to have a fully functional dashboard (including data scraping and exploring the various Plotly graphs). The complete source code for the visualisation is shown below and also available in my Github repo.

<script src="https://gist.github.com/cchanzl/d182756bf8ba8baf554aff34f082c5a6.js"></script>



