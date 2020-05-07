## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/macqian/Stat-153-Blog-Post/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/macqian/Stat-153-Blog-Post/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.



## Lebron James and Effort to Win

For the past 15 years, Lebron James has been one of the most dominant and recognized sports figures across the globe. But just how good has he been? To find out, we used a new metric called “Effort to Win” (E2W) that measures the physical effort Lebron James must exert in order to help his team win, and using that metric, we will forecast what his E2W will be for the first 10 games of the new NBA season. 

![Lebron James' E2W Time Series Plot](LBJ_E2W_Time_Series.png)

Looking at the chart above, we see Lebron has an **average E2W score of around 12** across his career thus far. However, there are two aspects of the graph that are concerning. First, the data itself follows a sinusoidal pattern, moving up and down as time increases. This creates variance, which for our situation, will be detrimental in creating accurate forecasts. Second, there are these large spikes that occur randomly throughout the time series. We hypothesize the reason for these spikes is because towards the end of each season, teams already know what their playoff seeding will be, so players like Lebron either take it easy or try extra hard for the last few games. 

To remove these two issues, we first used a technique called _differencing_ with respect to lag 1, which measures the change in Lebron’s E2W from one game to the next. We then created a time series plot and a ACF plot (which measures the correlation from game x and game x + i) using this new dataset to determine its fit. 

![Lebron James' E2W TS Plot with Differencing](LBJ_diff_TS.png)

![Lebron James' E2W ACF Plot with Differencing](LBJ_diff_ACF.png)

Looking at the new time series plot, the sinusoidal problem seems to be gone as there is a constant mean around 0. However, the spikes are still there, so we need to apply another statistical adjustment in order to account for them. We see in the ACF plot that there are two large spikes that fall outside the blue confidence intervals, one at lag 0 and one at lag 1. The lag 0 spike will always be there as a data point at time t will always have a correlation of 1 with itself. The spike at lag 1 tells us that the data set can most likely be fitted by a **moving average (MA) model**, specifically an **MA(1) model** as there is the large spike at lag 1. Using this final model, we arrive at our forecasts.



