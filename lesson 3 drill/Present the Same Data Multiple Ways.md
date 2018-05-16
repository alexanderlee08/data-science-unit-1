I choose https://www.kaggle.com/jessicali9530/honey-production/data as the data to use, which is about honey production.

# Single Continuous Variable 4 Ways
The variable in question is total production.  I limited this query to the state of Alabama and ordered the dataset by year.

1.
Here we see the mean with the variance in production, which is good if we want to get an idea of how much fluctuation there is.

```python
plt.boxplot(honey_prod)  # alpha just controls the opacity
plt.ylabel('Amount Produced in Thousands')
plt.legend(loc='upper right')
plt.title('Plot 1: Boxplot of AL')
plt.show()
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%201%20boxplot.png)

2.
This doesn't have historic data, but we get a better idea of where possible medians in production are, perhaps due to economic changes historically in the economy.

```python
plt.hist(honey_prod, color='red')  # alpha just controls the opacity
plt.xlabel('Amount Produced in Thousands')
plt.legend(loc='upper right')
plt.title('Plot 2: Hist of Honey Production in AL')
plt.show()
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%202%20hist.png)

In these last two plots I had to include the year.

3.
This gives us a production trend, so that we see it decreasing.  The colors are distracting though.

```python
sns.set(style="darkgrid")

g = sns.factorplot(x="year", y="totalprod", data=honey_prod_year,
                   size=6, kind="bar", palette="pastel", ci=95)
g.despine(left=True)
g.set_ylabels("Total Production")
g.set_xlabels("Year")
plt.title('Barplot: Production of Honey in AL')
plt.show()
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%203%20bar.png)

4.
This is a better trend as the colors are less distracting, but the colors still add too much information.

```python
sns.set(style="darkgrid")

g = sns.factorplot(x="year", y="totalprod", data=honey_prod_year,
                   size=6, kind="point", palette="pastel", ci=95)
g.despine(left=True)
g.set_ylabels("Total Production")
g.set_xlabels("Year")
plt.title('Barplot: Production of Honey in AL')
plt.show()
```
![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%204%20point.png)


# Two Continuous Variables 3 Ways

The two variables in question are total production and the price per pound.

1.
Here we see the price decreasing along with production.  So we see a clear trend relationship between lower price and greater production.

```python
plt.scatter(honey_prod_year['totalprod'], honey_prod_year['priceperlb'],  color='red')
plt.ylabel('Price per Pound')
plt.legend(loc='upper right')
plt.title('Plot 5: Scatter Plot of Honey Production in AL')
plt.show()
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%205.png)

2. 
In this chart I flipped the x and y so that the price is on the x axis.  This is confusing because we normally think of price as a function of volume.  The line connecting the history (the data is ordered by year) is also confusing since it's not relevant to any relationship we might want to see between price per pound and total volume produced.

```python
plt.plot(honey_prod_year['priceperlb'], honey_prod_year['totalprod'],  color='red')
plt.ylabel('Total Production')
plt.xlabel('Year')
plt.legend(loc='upper right')
plt.title('Plot 6: Plot of Honey Production in AL')
plt.show()
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%206.png)

3.
We see here the same plot as plot 5 but with a regression line.  The regression line suggests a trend as we read from left to right but it's really showing the average value in the relationship between the two variables.

```python
g = sns.lmplot(y='totalprod', 
               x='priceperlb',
               data=honey_prod_year,
               fit_reg=True, 
               ci=False,
               scatter_kws={'alpha':0.4}, 
               palette='pastel',
               lowess=True) # Using local weighing to fit a line.
g.set_xlabels("Price per Pound")
g.set_ylabels("Total Production")
plt.suptitle('Plot 7 Scatterplot Lowess: Regression line with Price per Pound and Total Production in AL')
plt.subplots_adjust(top=0.9)
plt.show()
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%207.png)


# One continuous and one categorical and six different ways.

So in this data there are 50 states.  I think that will be too much so I am just going to choose 3 different states, AL, HI and NY

1.
Here we see a wide variance in what NY has produced when compared to AL and HI.  This chart seems to waste space but I think its a fair comparison.

```
plt.hist(honey_prod_year_al, color='red',  alpha=.5,label='AL')  # alpha just controls the opacity
plt.hist(honey_prod_year_hi, color='blue', alpha=.5,label='HI')
plt.hist(honey_prod_year_ny, color='green', alpha=.5,label='NY')  
plt.xlabel('Total Production')
plt.legend(loc='upper right')
plt.title('Plot 8: Honey Production')
plt.show()
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%208%20v2.png)

2.
Here we see the range again, with the mean in a box plot.  The state is on the Y axis though so it seems a little weird.  I guess this chart would make sense if we were interested in where most of the honey was coming from instead of which state made what.

```python
ax = sns.boxplot(x='totalprod',y='state',data=ddf)  
plt.title('Plot 9: Boxplot of states by production')
sns.despine(offset=10, trim=True)
ax.set(xlabel='Total Production', ylabel='state')
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%209.png)

3.
This is the same data but a better comparison of state production.

```python
ax = sns.boxplot(x='state',y='totalprod',data=ddf)  
plt.title('Plot 10: Boxplot of states by production')
sns.despine(offset=10, trim=True)
ax.set(xlabel='Total Production', ylabel='state')
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%2010.png)

4.
Again we see the range of NY's production.  We get a better sense of the magnitude of difference in production.

```python
sns.set(style="darkgrid")

g = sns.factorplot(x="state", y="totalprod", data=ddf,
                   size=6, kind="bar", palette="pastel", ci=95)
g.despine(left=True)
g.set_ylabels("Total Production")
g.set_xlabels("State")
plt.title('Plot 11: Barplot of total production by state')
plt.show()
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%2011.png)

5.
This chart emphasizes the variance between their means of production but it also presents the difference in production.  Because the mean is just floating in space, I think the variance is emphasized.

```python
sns.set(style="whitegrid")

g = sns.factorplot(x="state", y="totalprod", data=ddf,
                   size=6, kind="point", palette="pastel",ci=95,dodge=True,join=False)
g.despine(left=True)
g.set_ylabels("Total Production")
g.set_xlabels("state")
plt.title('Plot 12: Pointplot: Meal Tips by Time and Gender')
plt.show()
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%2012.png)

6.
This chart gives us the difference in production historically, so its useful to see the trends.  NY really dropped whereas HI and AL didn't appear to do so, even though from the previous charts we know that AL's production dropped quite a bit.  NY skews the scale by a great deal.

```python
plt.plot(honey_prod_year['year'], honey_prod_year_al, color='b')
plt.plot(honey_prod_year['year'], honey_prod_year_hi, color='g')
plt.plot(honey_prod_year['year'], honey_prod_year_ny, color='r')
plt.ylabel('Production in Thousands')
plt.title('Plot 13: Comparison of Honey Production by state by year')
plt.show()
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/plot%2013.png)

# Challenge

I am going to look at the data for BTC.

The four variables I will look at will be the high, low, open and close pricing.  These four variables have a set relationship already, somewhat, since they are different values of the same thing at different periods.

I chart them below but limit the domain of the chart to one month.  Originally I had it longer but it was too hard to see what was going on with 4 variables in the chart.  We see that the most stable period in this chart is around the holidays, presumably because people are not trading.  Then we see a dip at the end of the year, perhaps reflecting the confidence of investors going into 2018.

```python
fig, (ax1) = plt.subplots(1, 1, sharex=True, figsize=(10, 5))

ax1.fill_between(BTC['Date'], BTC['High'], BTC['Low'], alpha = .5, color='red', label = 'High-Low')
ax1.set_ylabel('Price')
ax1.fill_between(BTC['Date'], BTC['Open'], BTC['Close'], alpha = .5, color = 'blue', label = 'Open-Close')

#ax2.fill_between(BTC['Date'], BTC['Open'], BTC['Close'])
#ax2.set_ylabel('between y1 and 1')
plt.legend(loc='upper left')
myLocator = mticker.MultipleLocator(4)
ax1.xaxis.set_major_locator(myLocator)
ax1.set_xlabel('Date')
ax1.set_title('BTC prices in Dec 2017')
```

![](https://github.com/alexanderlee08/data-science-unit-1/blob/master/lesson%203%20drill/challenge.png)
