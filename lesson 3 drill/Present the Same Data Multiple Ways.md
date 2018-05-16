I choose https://www.kaggle.com/jessicali9530/honey-production/data as the data to use.

# Single Continuous Variable 4 Ways
The variable in question is total production.  I limited this query to the state of Alabama and ordered the dataset by year.

1.
Here we see the mean with the variance in production, which is good if we want to get an idea of how much fluctuation there is.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%201%20boxplot.png)

2.
This doesn't have historic data, but we get a better idea of where possible medians in production are, perhaps due to economic changes historically in the economy.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%202%20hist.png)

In these last two plots I had to include the year.

3.
This gives us a production trend, so that we see it decreasing.  The colors are distracting though.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%203%20bar.png)

4.
This is a better trend as the colors are less distracting, but the colors still add too much information.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%204%20point.png)


# Two Continuous Variables 3 Ways

The two variables in question are total production and the price per pound.

1.
Here we see the price decreasing along with production.  So we see a clear trend relationship between lower price and greater production.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%205.png)

2. 
In this chart I flipped the x and y so that the price is on the x axis.  This is confusing because we normally think of price as a function of volume.  The line connecting the history (the data is ordered by year) is also confusing since it's not relevant to any relationship we might want to see between price per pound and total volume produced.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%206.png)

3.
We see here the same plot as plot 5 but with a regression line.  The regression line suggests a trend as we read from left to right but it's really showing the average value in the relationship between the two variables.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%207.png)


# One continuous and one categorical and six different ways.

So in this data there are 50 states.  I think that will be too much so I am just going to choose 3 different states, AL, HI and NY

1.
Here we see a wide variance in what NY has produced when compared to AL and HI.  This chart seems to waste space but I think its a fair comparison.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%208%20v2.png)

2.
Here we see the range again, with the mean in a box plot.  The state is on the Y axis though so it seems a little weird.  I guess this chart would make sense if we were interested in where most of the honey was coming from instead of which state made what.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%209.png)

3.
This is the same data but a better comparison of state production.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%2010.png)

4.
Again we see the range of NY's production.  We get a better sense of the magnitude of difference in production.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%2011.png)

5.
This chart emphasizes the variance between their means of production but it also presents the difference in production.  Because the mean is just floating in space, I think the variance is emphasized.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%2012.png)

6.
This chart gives us the difference in production historically, so its useful to see the trends.  NY really dropped whereas HI and AL didn't appear to do so, even though from the previous charts we know that AL's production dropped quite a bit.  NY skews the scale by a great deal.

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%2013.png)

# Challenge

I am going to look at the data for BTC.


