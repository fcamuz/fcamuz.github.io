---
layout: post
title:      "Chartify is a Python library for easy visualization"
date:       2020-02-25 14:03:59 -0500
permalink:  chartify_is_a_python_library_that_makes_it_easy_charts
---


Chartify is an alternative visulization tool such as Seaborn in Python. It is an open-source Python library that wraps Bokeh to make it easier for data scientists to create charts.

I will show you only a few plots here in this blog. But there are a lot more you can do with this library and many parameters that you may change to create chart spesific to your needs. To see all other option you may visit the . 
![Chartify Github Repo](https://github.com/spotify/chartify)


## Installation

Installation
1. Chartify can be installed via pip:
```python
!pip install chartify
```
2. Install chromedriver requirement (Optional. Needed for PNG output):
Install google chrome.
Download the appropriate version of chromedriver for your OS.
Copy the executable file to a directory within your PATH.

PATH is where your executiable files are stored in your computer. There might be multiple directories that functions as PATH.  View directorys in your PATH variable by typing  echo $PATH 
to your terminal. Once you figured, copy chromedriver to the appropriate directory, e.g.: cp chromedriver /usr/local/bin



## Import

After installation you may use chartify libary by importing to your notebook. I also imported numpy and pandas library to use transorming data in our example in this notebook.

```python
import chartify
import numpy as np
import pandas as pd
```

## Example data

Lets generate some example data. 

``` python
chartify.examples.example_data().head(10)
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>country</th>
      <th>fruit</th>
      <th>unit_price</th>
      <th>quantity</th>
      <th>total_price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>2017-10-21</td>
      <td>US</td>
      <td>Banana</td>
      <td>0.303711</td>
      <td>4</td>
      <td>1.214846</td>
    </tr>
    <tr>
      <td>1</td>
      <td>2017-05-30</td>
      <td>JP</td>
      <td>Banana</td>
      <td>0.254109</td>
      <td>4</td>
      <td>1.016436</td>
    </tr>
    <tr>
      <td>2</td>
      <td>2017-05-21</td>
      <td>CA</td>
      <td>Banana</td>
      <td>0.268635</td>
      <td>4</td>
      <td>1.074539</td>
    </tr>
    <tr>
      <td>3</td>
      <td>2017-09-18</td>
      <td>BR</td>
      <td>Grape</td>
      <td>2.215277</td>
      <td>2</td>
      <td>4.430554</td>
    </tr>
    <tr>
      <td>4</td>
      <td>2017-12-08</td>
      <td>US</td>
      <td>Banana</td>
      <td>0.308337</td>
      <td>5</td>
      <td>1.541687</td>
    </tr>
    <tr>
      <td>5</td>
      <td>2017-06-05</td>
      <td>GB</td>
      <td>Apple</td>
      <td>0.870118</td>
      <td>2</td>
      <td>1.740235</td>
    </tr>
    <tr>
      <td>6</td>
      <td>2017-09-05</td>
      <td>JP</td>
      <td>Banana</td>
      <td>0.279179</td>
      <td>7</td>
      <td>1.954252</td>
    </tr>
    <tr>
      <td>7</td>
      <td>2017-08-27</td>
      <td>CA</td>
      <td>Apple</td>
      <td>1.025265</td>
      <td>4</td>
      <td>4.101059</td>
    </tr>
    <tr>
      <td>8</td>
      <td>2017-09-14</td>
      <td>CA</td>
      <td>Apple</td>
      <td>1.078831</td>
      <td>4</td>
      <td>4.315324</td>
    </tr>
    <tr>
      <td>9</td>
      <td>2017-05-26</td>
      <td>GB</td>
      <td>Grape</td>
      <td>1.840909</td>
      <td>2</td>
      <td>3.681818</td>
    </tr>
  </tbody>
</table>
</div>


## Example  Plots

Now we can do some transformation and create various types of plots using cartify. Here are some exapmles.

## Scatter

```python
ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
ch.plot.scatter(
    data_frame=data,
    x_column='date',
    y_column='unit_price')
ch.set_title("Scatterplot")
ch.set_subtitle("Plot two numeric values.")
ch.show('png')
```

![png](Examples/output_8_1.png)

![png](https://github.com/fcamuz/fcamuz.github.io/tree/master/_posts/Examples/output_8_1.png)

You may define 

```python   
# Plot the data
ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
ch.plot.scatter(
    data_frame=data,
    x_column='date',
    y_column='unit_price',
    size_column='quantity',
    color_column='fruit')
ch.set_title("Scatterplot")
ch.set_subtitle("Optional 'color_column' argument for grouping by color.")
ch.show('png')
 ```   



![png](output_8_5.png)


## Text

```python
# Manipulate the data
price_and_quantity_by_country = (
    data.groupby('country')[['total_price', 'quantity']].sum()
    .reset_index())
print(price_and_quantity_by_country.head())
        
      country  total_price  quantity
    0      BR   208.553175       215
    1      CA   473.922173       659
    2      GB   370.257657       446
    3      JP   263.204503       424
    4      US   645.058909      1134

# Plot the data
ch = chartify.Chart(blank_labels=True)
ch.plot.scatter(
    data_frame=price_and_quantity_by_country,
    x_column='total_price',
    y_column='quantity',
    color_column='country')
ch.style.color_palette.reset_palette_order()
ch.plot.text(
    data_frame=price_and_quantity_by_country,
    x_column='total_price',
    y_column='quantity',
    text_column='country',
    color_column='country',
    x_offset=1,
    y_offset=-1,
    font_size='10pt')
ch.set_title("Text")
ch.set_subtitle("Labels for specific observations.")
ch.show('png')
    
```

![png](output_10_1.png)


## Line

```python

price_by_date_and_country = (
    data.groupby(['date', 'fruit'])['total_price'].sum()
    .reset_index()  # Move 'date' and 'country' from index to column
    )
print(price_by_date_and_country.head())

    date   fruit  total_price
0 2017-01-10   Apple     1.808778
1 2017-01-12  Orange     0.829621
2 2017-01-22   Grape     1.998476
3 2017-01-27  Banana     1.390764
4 2017-01-28   Apple     2.658465

ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
ch.set_title("Line charts - Grouped by color")
ch.plot.line(
    # Data must be sorted by x column
    data_frame=price_by_date_and_country.sort_values('date'),
    x_column='date',
    y_column='total_price',
    color_column='fruit')
ch.show('png')
    
```


![png](output_12_3.png)


## Area

```python
# Sum price grouped by date
price_by_date = (data.groupby(['date'])['total_price'].agg(
    ['mean', 'std', 'count'])
    .loc['2017-12-01':].assign(
        lower_ci=lambda x: x['mean'] - 1.96 * x['std'] / x['count']**.5,
        upper_ci=lambda x: x['mean'] + 1.96 * x['std'] / x['count']**.5)
    .reset_index())
print(price_by_date.head())

    date      mean       std  count  lower_ci  upper_ci
0 2017-12-01  2.130242  1.723854      3  0.179518  4.080967
1 2017-12-02  1.801198  1.385051     10  0.942735  2.659662
2 2017-12-03  2.157626  1.163018      7  1.296050  3.019202
3 2017-12-04  0.923048  0.472394      4  0.460102  1.385994
4 2017-12-05  2.179000  1.258695      7  1.246546  3.111454

# Plot the data
ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
ch.set_title("Area with second_y_column")
ch.set_subtitle(
    "Use alone or combined with line graphs to represent confidence."
)
ch.plot.area(
    data_frame=price_by_date,
    x_column='date',
    y_column='lower_ci',
    second_y_column='upper_ci')
# Reset to ensure same color of line & shaded interval
ch.style.color_palette.reset_palette_order()
ch.plot.line(
    data_frame=price_by_date,
    x_column='date',
    y_column='mean')
ch.show('png')
```

![png](output_14_5.png)


## Bar plot

```python       
ch = chartify.Chart(x_axis_type='categorical', blank_labels=True)
ch.set_title("Vertical bar plot with labels")
ch.set_subtitle("Hidden y-axis")
ch.plot.bar(
    data_frame=quantity_by_fruit,
    categorical_columns='fruit',
    numeric_column='quantity',
    color_column='fruit')
ch.style.color_palette.reset_palette_order()
ch.plot.text(
    data_frame=quantity_by_fruit,
    categorical_columns='fruit',
    numeric_column='quantity',
    text_column='quantity',
    color_column='fruit')
# Adjust the axis range to prevent clipping of the text labels.
ch.axes.set_yaxis_range(0, 1200)
ch.axes.hide_yaxis()
ch.show('png')
```   

![png](output_17_7.png)


# Bar (grouped)

```python
quantity_by_fruit_and_country = (data.groupby(
    ['fruit', 'country'])['quantity'].sum().reset_index())
print(quantity_by_fruit_and_country.head())
    
    fruit country  quantity
0  Apple      BR        57
1  Apple      CA       144
2  Apple      GB       177
3  Apple      JP        65
4  Apple      US       165

# Plot the data
ch = chartify.Chart(blank_labels=True, x_axis_type='categorical')
ch.set_title("Grouped bar chart")
ch.set_subtitle(
    "Pass a list to group by multiple factors. Color grouped by 'fruit'")
ch.plot.bar(
    data_frame=quantity_by_fruit_and_country,
    categorical_columns=['fruit', 'country'],
    numeric_column='quantity',
    color_column='fruit')
ch.show('png')
```



![png](output_19_1.png)


```python   
ch = chartify.Chart(blank_labels=True, x_axis_type='categorical')
ch.set_title("Grouped bar chart - Color groupings")
ch.set_subtitle(
    "Change color independent of the axis factors. Color grouped by 'country'"
)
ch.plot.bar(
    data_frame=quantity_by_fruit_and_country,
    categorical_columns=['fruit', 'country'],
    numeric_column='quantity',
    color_column='country')
ch.show('png')
```
![png](output_19_3.png)


```python
    
ch = chartify.Chart(blank_labels=True, x_axis_type='categorical')
ch.set_title("Grouped bar chart - Factor order")
ch.set_subtitle("Change categorical order with 'categorical_order_by'.")
ch.plot.bar(
    data_frame=quantity_by_fruit_and_country,
    categorical_columns=['country', 'fruit'],
    numeric_column='quantity',
    color_column='country',
    categorical_order_by='labels',
    categorical_order_ascending=True)
ch.axes.set_xaxis_tick_orientation('vertical')
ch.show('png')
```
    



![png](output_19_7.png)


## Lollipop


```python
quantity_by_fruit_and_country = (data.groupby(
    ['fruit', 'country'])['quantity'].sum().reset_index())
print(quantity_by_fruit_and_country.head())
    
    fruit country  quantity
0  Apple      BR        57
1  Apple      CA       144
2  Apple      GB       177
3  Apple      JP        65
4  Apple      US       165

# Plot the data
ch = chartify.Chart(blank_labels=True, y_axis_type='categorical')
ch.set_title("Lollipop chart")
ch.set_subtitle("Same options as bar plot")
ch.plot.lollipop(
    data_frame=quantity_by_fruit_and_country,
    categorical_columns=['country', 'fruit'],
    numeric_column='quantity',
    color_column='country')
ch.show('png')
```    

![png](output_23_1.png)


## Bar (Stacked)

```python
quantity_by_fruit_and_country = (data.groupby(
    ['fruit', 'country'])['quantity'].sum().reset_index())
print(quantity_by_fruit_and_country.head())
    
    fruit country  quantity
0  Apple      BR        57
1  Apple      CA       144
2  Apple      GB       177
3  Apple      JP        65
4  Apple      US       165

# Plot the data
(chartify.Chart(blank_labels=True,
                x_axis_type='categorical')
    .set_title("Stacked bar chart")
    .set_subtitle("Stack columns by a categorical factor.")
    .plot.bar_stacked(
        data_frame=quantity_by_fruit_and_country,
        categorical_columns=['fruit'],
        numeric_column='quantity',
        stack_column='country',
        normalize=False)
    .show('png'))
```    

![png](output_25_1.png)


```python
 # Add a column for labels.
# Note: Null labels will not be added to the chart.
quantity_by_fruit_and_country['label'] = np.where(
quantity_by_fruit_and_country['country'].isin(['US', 'CA']),
quantity_by_fruit_and_country['quantity'],
None)

(chartify.Chart(blank_labels=True, x_axis_type='categorical')
.set_title("Stacked bar with labels")
.set_subtitle("")
.plot.bar_stacked(
    data_frame=quantity_by_fruit_and_country,
    categorical_columns=['fruit'],
    numeric_column='quantity',
    stack_column='country',
    normalize=True,
    stack_order=country_order)
.plot.text_stacked(
    data_frame=quantity_by_fruit_and_country,
    categorical_columns=['fruit'],
    numeric_column='quantity',
    stack_column='country',
    text_column='label',
    normalize=True,
    stack_order=country_order,
    # Set the text color otherwise it will take
    # The next color in the color palette.
    text_color='white'
    )
.show('png'))
```    
![png](output_25_7.png)

## Parallel coordinate plot
```python
total_quantity_by_fruit_and_country = (data.groupby(
    ['fruit', 'country'])['quantity'].sum().reset_index())
print(total_quantity_by_fruit_and_country.head())
    
    fruit country  quantity
0  Apple      BR        57
1  Apple      CA       144
2  Apple      GB       177
3  Apple      JP        65
4  Apple      US       165

# Plot the data
ch = chartify.Chart(blank_labels=True, x_axis_type='categorical')
ch.set_title("Parallel coordinate charts")
ch.set_subtitle("")
ch.plot.parallel(
    data_frame=total_quantity_by_fruit_and_country,
    categorical_columns='fruit',
    numeric_column='quantity',
    color_column='country')
ch.show('png')
```

![png](output_27_1.png)


## Heatmap
```python
```average_price_by_fruit_and_country = (data.groupby(
    ['fruit', 'country'])['total_price'].mean().reset_index())


# Plot the data
(chartify.Chart(
    blank_labels=True,
    x_axis_type='categorical',
    y_axis_type='categorical')
    .plot.heatmap(
    data_frame=average_price_by_fruit_and_country,
    x_column='fruit',
    y_column='country',
    color_column='total_price',
    text_column='total_price',
    text_color='white')
    .axes.set_xaxis_label('Fruit')
    .axes.set_yaxis_label('Country')
    .set_title('Heatmap')
    .set_subtitle("Plot numeric value grouped by two categorical values")
    .show('png'))
```

![png](output_31_1.png)

## Single density axis

```python
# Plot the data
ch = chartify.Chart(blank_labels=True, y_axis_type='density')
ch.set_title("KDE plot + Histogram")
ch.plot.kde(
    data_frame=data,
    values_column='unit_price',
    color_column='fruit')
ch.style.color_palette.reset_palette_order()
ch.plot.histogram(
    data_frame=data,
    values_column='unit_price',
    color_column='fruit',
    method='density')
ch.show('png')
```    

![png](output_34_3.png)



## Radar chart

```python

total_by_fruit_and_country = data.groupby(['fruit', 'country'])['quantity'].sum().reset_index()
print(total_by_fruit_and_country.head())

fruit country  quantity
0  Apple      BR        57
1  Apple      CA       144
2  Apple      GB       177
3  Apple      JP        65
4  Apple      US       165

ch = chartify.RadarChart(True, layout='slide_50%')
ch.set_title('Radar Area Chart')
ch.set_subtitle("Each vertex plotted counterclockwise starting from top")
ch.plot.text(total_by_fruit_and_country.groupby('country')['quantity'].max().reset_index(),
                'quantity',
                text_column='country',
                text_align='center')
ch.plot.area(total_by_fruit_and_country, 'quantity', color_column='fruit')
ch.axes.hide_yaxis()
ch.axes.hide_xaxis()
ch.set_legend_location('outside_bottom')
ch.show('png')
 ``` 

![png](output_40_1.png)

## Color Palettes
There is a large color palettes that you can use in chartify. 

```python
chartify.color_palettes
```
    Color Palettes: 
    'Category20'
    'Category10'
    'Colorblind'
    'Dark2'
    'Pastel1'
    'RdBu'
    'RdGy'
    'Greys'
    'Greens'
    'Blues'
    'Reds'
    'Oranges'
    'All colors'


```python
chartify.color_palettes.show()
```

<h2>Color Palettes</h2><div><div style='padding: 10px; margin: 5px;'>
                  <h3>Category20</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #1f77b4;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#1f77b4',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ff7f0e;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#ff7f0e',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #2ca02c;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#2ca02c',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #d62728;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#d62728',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #9467bd;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#9467bd',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #8c564b;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#8c564b',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #e377c2;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#e377c2',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #7f7f7f;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#7f7f7f',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #bcbd22;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#bcbd22',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #17becf;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#17becf',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #aec7e8;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#aec7e8',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffbb78;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#ffbb78',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #98df8a;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#98df8a',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ff9896;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#ff9896',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #c5b0d5;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#c5b0d5',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #c49c94;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#c49c94',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f7b6d2;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#f7b6d2',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #c7c7c7;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#c7c7c7',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #dbdb8d;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#dbdb8d',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #9edae5;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#9edae5',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>Category10</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #1f77b4;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#1f77b4',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ff7f0e;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#ff7f0e',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #2ca02c;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#2ca02c',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #d62728;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#d62728',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #9467bd;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#9467bd',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #8c564b;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#8c564b',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #e377c2;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#e377c2',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #7f7f7f;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#7f7f7f',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #bcbd22;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#bcbd22',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #17becf;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#17becf',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>Colorblind</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #0072b2;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#0072b2',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #e69f00;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#e69f00',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f0e442;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#f0e442',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #009e73;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#009e73',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #56b4e9;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#56b4e9',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #d55e00;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#d55e00',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #cc79a7;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#cc79a7',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #000;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'black',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>Dark2</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #1b9e77;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#1b9e77',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #d95f02;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#d95f02',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #7570b3;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#7570b3',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #e7298a;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#e7298a',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #66a61e;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#66a61e',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #e6ab02;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#e6ab02',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #a6761d;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#a6761d',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #666;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#666',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>Pastel1</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #fbb4ae;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#fbb4ae',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #b3cde3;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#b3cde3',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ccebc5;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#ccebc5',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #decbe4;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#decbe4',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fed9a6;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#fed9a6',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffc;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#ffc',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #e5d8bd;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#e5d8bd',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fddaec;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#fddaec',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f2f2f2;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#f2f2f2',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>RdBu</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #67a9cf;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#67a9cf',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f7f7f7;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#f7f7f7',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ef8a62;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#ef8a62',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>RdGy</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #404040;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#404040',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #bababa;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#bababa',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fff;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'white',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f4a582;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#f4a582',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ca0020;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#ca0020',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>Greys</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #d9d9d9;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#d9d9d9',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #bdbdbd;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#bdbdbd',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #969696;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#969696',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #737373;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#737373',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #525252;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#525252',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #252525;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#252525',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #000;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'black',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>Greens</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #c7e9c0;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#c7e9c0',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #a1d99b;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#a1d99b',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #74c476;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#74c476',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #41ab5d;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#41ab5d',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #238b45;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#238b45',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #006d2c;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#006d2c',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #00441b;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#00441b',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>Blues</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #c6dbef;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#c6dbef',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #9ecae1;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#9ecae1',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #6baed6;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#6baed6',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #4292c6;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#4292c6',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #2171b5;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#2171b5',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #08519c;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#08519c',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #08306b;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#08306b',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>Reds</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #fcbba1;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#fcbba1',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fc9272;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#fc9272',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fb6a4a;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#fb6a4a',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ef3b2c;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#ef3b2c',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #cb181d;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#cb181d',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #a50f15;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#a50f15',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #67000d;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#67000d',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>Oranges</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #fdd0a2;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#fdd0a2',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fdae6b;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#fdae6b',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fd8d3c;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#fd8d3c',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f16913;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#f16913',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #d94801;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#d94801',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #a63603;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#a63603',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #7f2704;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'#7f2704',</div></div> <div style='padding: 10px; margin: 5px;'>
                  <h3>All colors</h3><div style="width: 200px;
                        height: 20px;
                        background-color: #ffb6c1;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightPink',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffc0cb;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'pink',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #dc143c;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'crimson',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #db7093;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'PaleVioletRed',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fff0f5;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LavenderBlush',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ff69b4;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'HotPink',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ff1493;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DeepPink',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #c71585;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MediumVioletRed',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #d02090;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'VioletRed',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #da70d6;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'orchid',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #800080;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'purple',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #d8bfd8;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'thistle',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #dda0dd;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'plum',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f0f;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'magenta',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #8b008b;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkMagenta',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ee82ee;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'violet',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ba55d3;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MediumOrchid',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #9400d3;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkViolet',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #9932cc;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkOrchid',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #4b0082;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'indigo',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #8a2be2;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'BlueViolet',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #9370db;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MediumPurple',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #7b68ee;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MediumSlateBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #483d8b;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkSlateBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #8470ff;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightSlateBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #6a5acd;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'SlateBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #00008b;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #000080;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'navy',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #0000cd;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MediumBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #00f;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'blue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #191970;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MidnightBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #e6e6fa;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'lavender',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f8f8ff;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'GhostWhite',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #4169e1;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'RoyalBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #6495ed;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'CornflowerBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #53585f;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'dark grey',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #b0c4de;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightSteelBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #708090;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'SlateGray',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #789;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightSlateGray',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #1e90ff;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DodgerBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f0f8ff;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'AliceBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #4682b4;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'SteelBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #87cefa;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightSkyBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #87ceeb;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'SkyBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #00bfff;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DeepSkyBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #add8e6;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #b0e0e6;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'PowderBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #5f9ea0;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'CadetBlue',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #00ced1;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkTurquoise',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #008b8b;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkCyan',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #0ff;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'cyan',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #2f4f4f;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkSlateGray',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #afeeee;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'PaleTurquoise',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #e0ffff;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightCyan',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f0ffff;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'azure',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #48d1cc;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MediumTurquoise',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #20b2aa;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightSeaGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #40e0d0;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'turquoise',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #7fffd4;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'aquamarine',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #66cdaa;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MediumAquamarine',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #00fa9a;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MediumSpringGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f5fffa;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MintCream',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #00ff7f;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'SpringGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #3cb371;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MediumSeaGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #2e8b57;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'SeaGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #008000;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'green',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #0f0;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'lime',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #228b22;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'ForestGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #8fbc8f;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkSeaGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #90ee90;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #98fb98;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'PaleGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f0fff0;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'honeydew',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #006400;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #32cd32;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LimeGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #7cfc00;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LawnGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #7fff00;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'chartreuse',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #adff2f;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'GreenYellow',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #556b2f;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkOliveGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #9acd32;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'YellowGreen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #6b8e23;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'OliveDrab',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fafad2;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightGoldenrodYellow',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #808000;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'olive',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f5f5dc;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'beige',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ff0;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'yellow',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffffe0;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightYellow',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fffff0;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'ivory',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #bdb76b;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkKhaki',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #eee8aa;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'PaleGoldenrod',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f0e68c;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'khaki',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fffacd;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LemonChiffon',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffd700;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'gold',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #eedd82;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightGoldenrod',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fff8dc;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'cornsilk',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #daa520;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'goldenrod',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #b8860b;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkGoldenrod',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fffaf0;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'FloralWhite',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fdf5e6;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'OldLace',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f5deb3;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'wheat',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffa500;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'orange',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffe4b5;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'moccasin',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffefd5;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'PapayaWhip',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffebcd;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'BlanchedAlmond',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffdead;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'NavajoWhite',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #d2b48c;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'tan',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #faebd7;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'AntiqueWhite',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #deb887;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'burlywood',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ff8c00;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkOrange',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffe4c4;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'bisque',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #faf0e6;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'linen',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #cd853f;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'peru',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffdab9;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'PeachPuff',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f4a460;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'SandyBrown',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #8b4513;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'SaddleBrown',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #d2691e;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'chocolate',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fff5ee;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'seashell',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #a0522d;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'sienna',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffa07a;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightSalmon',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ff4500;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'OrangeRed',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ff7f50;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'coral',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #e9967a;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkSalmon',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ff6347;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'tomato',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fa8072;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'salmon',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #ffe4e1;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'MistyRose',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #000;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'black',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #696969;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DimGray',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #800000;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'maroon',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #808080;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'gray',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #8b0000;
                        color: white;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkRed',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #a52a2a;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'brown',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #a9a9a9;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'DarkGray',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #b22222;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'firebrick',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #bc8f8f;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'RosyBrown',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #c0c0c0;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'silver',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #cd5c5c;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'IndianRed',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #d3d3d3;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightGray',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #dcdcdc;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'gainsboro',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f08080;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'LightCoral',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f5f5f5;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'WhiteSmoke',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #f00;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'red',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fffafa;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'snow',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #fff;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'white',</div> <div style="width: 200px;
                        height: 20px;
                        background-color: #e8e8e8;
                        color: black;
                        padding: 2px;
                        margin: 2px;
                        display: block;">'light grey',</div></div></div>



