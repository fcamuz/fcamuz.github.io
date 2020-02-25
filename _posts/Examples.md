# Examples


```python
# Copyright (c) 2017-2018 Spotify AB
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
import chartify
```



# Blank charts


```python
chartify.examples.chart_blank()
```

    
        import chartify
    
        # Blank charts tell you how to fill in the labels
        ch = chartify.Chart()
        ch.show('png')
    


    WARNING:bokeh.core.validation.check:W-1000 (MISSING_RENDERERS): Plot has no renderers: Figure(id='1001', ...)



![png](output_3_2.png)


# Example data


```python
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



# Both Numerical Axes

## Scatter


```python
print(chartify.examples.plot_scatter.__doc__)
chartify.examples.plot_scatter()
```

    Scatter plot.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                x_column (str): Column name to plot on the x axis.
                y_column (str): Column name to plot on the y axis.
                size_column (str, optional): Column name of numerical values
                    to plot on the size dimension.
                color_column (str, optional): Column name to group by on
                    the color dimension.
                color_order (list, optional): List of values within the
                    'color_column' for specific sorting of the colors.
                alpha (float): Alpha value.
                marker (str): marker type. Valid types:
                    'asterisk', 'circle', 'circle_cross', 'circle_x', 'cross',
                    'diamond', 'diamond_cross', 'hex', 'inverted_triangle',
                    'square', 'square_x', 'square_cross', 'triangle',
                    'x', '*', '+', 'o', 'ox', 'o+'
            
    
        import numpy as np
        import pandas as pd
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
        
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
        ch.plot.scatter(
            data_frame=data,
            x_column='date',
            y_column='unit_price')
        ch.set_title("Scatterplot")
        ch.set_subtitle("Plot two numeric values.")
        ch.show('png')
    



![png](output_8_1.png)


    
        # Plot the data
        ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
        ch.plot.scatter(
            data_frame=data,
            x_column='date',
            y_column='unit_price',
            size_column='quantity')
        ch.set_title("Scatterplot")
        ch.set_subtitle(
            "Optional 'size_column' argument for changing scatter size.")
        ch.show('png')
    



![png](output_8_3.png)


    
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
    



![png](output_8_5.png)


## Text


```python
print(chartify.examples.plot_text.__doc__)
chartify.examples.plot_text()
```

    Text plot.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                x_column (str): Column name to plot on the x axis.
                y_column (str): Column name to plot on the y axis.
                text_column (str): Column name to plot as text labels.
                color_column (str, optional): Column name to group by on the
                    color dimension.
                color_order (list, optional): List of values within the
                    'color_column' for specific sorting of the colors.
                font_size (str, optional): Size of text.
                x_offset (int, optional): # of pixels for horizontal text offset.
                    Can be negative. Default: 0.
                y_offset (int, optional): # of pixels for vertical text offset.
                    Can be negative. Default: 0.
                angle (int): Degrees from horizontal for text rotation.
                text_color (str): Color name or hex value.
                    See chartify.color_palettes.show() for available color names.
                    If omitted, will default to the next color in the
                    current color palette.
            
    
        import chartify
    
        data = chartify.examples.example_data()
    
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
    



![png](output_10_1.png)


## Line


```python
print(chartify.examples.plot_line.__doc__)
chartify.examples.plot_line()
```

    Line Chart.
    
            Note:
                This method will not automatically sort the x-axis.
                Try sorting the axis if the line graph looks strange.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                x_column (str): Column name to plot on the x axis.
                y_column (str): Column name to plot on the y axis.
                color_column (str, optional): Column name to group by on
                    the color dimension.
                color_order (list, optional): List of values within the
                    'color_column' for specific sorting of the colors.
                line_dash (str, optional): Dash style for the line. One of:
                    - 'solid'
                    - 'dashed'
                    - 'dotted'
                    - 'dotdash'
                    - 'dashdot'
                line_width (int, optional): Width of the line
                alpha (float): Alpha value.
            
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        # Sum price grouped by date
        price_by_date = (
            data.groupby('date')['total_price'].sum()
            .reset_index()  # Move 'date' from index to column
            )
        print(price_by_date.head())
        
            date  total_price
    0 2017-01-10     1.808778
    1 2017-01-12     0.829621
    2 2017-01-22     1.998476
    3 2017-01-27     1.390764
    4 2017-01-28     2.658465
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
        ch.set_title("Line charts")
        ch.set_subtitle("Plot two numeric values connected by an ordered line.")
        ch.plot.line(
            # Data must be sorted by x column
            data_frame=price_by_date.sort_values('date'),
            x_column='date',
            y_column='total_price')
        ch.show('png')
    



![png](output_12_1.png)


    
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
    



![png](output_12_3.png)


# Area


```python
print(chartify.examples.plot_area.__doc__)
chartify.examples.plot_area()
```

    Area plot.
    
            Note:
                - When a single y_column is passed: Shade area between the
                    y_values and zero.
                - Use `stacked` argument for stacked areas.
                - When both y_column and second_y_column are passed:
                    Shade area between the two y_columns.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                x_column (str): Column name to plot on the x axis.
                y_column (str): Column name to plot on the y axis.
                second_y_column (str, optional): Column name to plot on
                    the y axis.
                color_column (str, optional): Column name to group by on
                    the color dimension.
                color_order (list, optional): List of values within the
                    'color_column' for specific sorting of the colors.
                stacked (bool, optional): Stacked the areas.
                    Only applicable with a single y_column.
                    Default: False.
            
    
        import pandas as pd
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        total_quantity_by_month_and_fruit = (data.groupby(
            [data['date'] + pd.offsets.MonthBegin(-1), 'fruit'])['quantity'].sum()
            .reset_index().rename(columns={'date': 'month'})
            .sort_values('month'))
        print(total_quantity_by_month_and_fruit.head())
        
           month   fruit  quantity
    0 2017-01-01   Apple         7
    1 2017-01-01  Banana         6
    2 2017-01-01   Grape         1
    3 2017-01-01  Orange         2
    4 2017-02-01   Apple         8
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
        ch.set_title("Stacked area")
        ch.set_subtitle("Represent changes in distribution.")
        ch.plot.area(
            data_frame=total_quantity_by_month_and_fruit,
            x_column='month',
            y_column='quantity',
            color_column='fruit',
            stacked=True)
        ch.show('png')
    



![png](output_14_1.png)


    
        ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
        ch.set_title("Unstacked area")
        ch.set_subtitle("Show overlapping values. Automatically adjusts opacity.")
        ch.plot.area(
            data_frame=total_quantity_by_month_and_fruit,
            x_column='month',
            y_column='quantity',
            color_column='fruit',
            stacked=False)
        ch.show('png')
    



![png](output_14_3.png)


    
    
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
    



![png](output_14_5.png)


# Numeric axis & Categorical Axis

## Bar plot


```python
print(chartify.examples.plot_bar.__doc__)
chartify.examples.plot_bar()
```

    Bar chart.
    
            Note:
                To change the orientation set x_axis_type or y_axis_type
                argument of the Chart object.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                categorical_columns (str or list): Column name to plot on
                    the categorical axis.
                numeric_column (str): Column name to plot on the numerical axis.
                color_column (str, optional): Column name to group by on
                    the color dimension.
                color_order (list, optional): List of values within the
                    'color_column' for specific color sort.
                categorical_order_by (str or array-like, optional):
                    Dimension for ordering the categorical axis. Default 'values'.
                    - 'values': Order categorical axis by the numerical
                        axis values. Default.
                    - 'labels': Order categorical axis by the categorical labels.
                    - array-like object (list, tuple, np.array): New labels
                        to conform the categorical axis to.
                categorical_order_ascending (bool, optional): Sort order of the
                    categorical axis. Default False.
            
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        quantity_by_fruit = (data.groupby('fruit')['quantity'].sum().reset_index())
    
        print(quantity_by_fruit.head())
        
        fruit  quantity
    0   Apple       608
    1  Banana      1076
    2   Grape       332
    3  Orange       862
    
        ch = chartify.Chart(blank_labels=True, x_axis_type='categorical')
        ch.set_title("Vertical bar plot")
        ch.set_subtitle("Automatically sorts by value counts.")
        ch.plot.bar(
            data_frame=quantity_by_fruit,
            categorical_columns='fruit',
            numeric_column='quantity')
        ch.show('png')
    



![png](output_17_1.png)


    
        ch = chartify.Chart(blank_labels=True, x_axis_type='categorical')
        ch.set_title("Vertical bar plot - Label sort")
        ch.set_subtitle("Set `categorical_order_by` to sort by labels")
        ch.plot.bar(
            data_frame=quantity_by_fruit,
            categorical_columns='fruit',
            numeric_column='quantity',
            categorical_order_by='labels',
            categorical_order_ascending=True)
        ch.show('png')
    



![png](output_17_3.png)


    
        ch = chartify.Chart(blank_labels=True, y_axis_type='categorical')
        ch.set_title("Horizontal bar plot")
        ch.set_subtitle("Horizontal with color grouping")
        ch.plot.bar(
            data_frame=quantity_by_fruit,
            categorical_columns='fruit',
            numeric_column='quantity',
            color_column='fruit')
        ch.show('png')
    



![png](output_17_5.png)


    
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
    



![png](output_17_7.png)


## Bar (grouped)


```python
print(chartify.examples.plot_bar_grouped.__doc__)
chartify.examples.plot_bar_grouped()
```

    
        Grouped bar example.
    
        ch.plot.bar() docstring:
        Bar chart.
    
            Note:
                To change the orientation set x_axis_type or y_axis_type
                argument of the Chart object.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                categorical_columns (str or list): Column name to plot on
                    the categorical axis.
                numeric_column (str): Column name to plot on the numerical axis.
                color_column (str, optional): Column name to group by on
                    the color dimension.
                color_order (list, optional): List of values within the
                    'color_column' for specific color sort.
                categorical_order_by (str or array-like, optional):
                    Dimension for ordering the categorical axis. Default 'values'.
                    - 'values': Order categorical axis by the numerical
                        axis values. Default.
                    - 'labels': Order categorical axis by the categorical labels.
                    - array-like object (list, tuple, np.array): New labels
                        to conform the categorical axis to.
                categorical_order_ascending (bool, optional): Sort order of the
                    categorical axis. Default False.
            
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
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
    



![png](output_19_1.png)


    
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
    



![png](output_19_3.png)


    
        ch = chartify.Chart(blank_labels=True, x_axis_type='categorical')
        ch.set_title("Grouped bar chart - Group hierarchy order")
        ch.set_subtitle(
            "Change chage order of 'categorical_column' list to switch grouping hierarchy."
        )
        ch.plot.bar(
            data_frame=quantity_by_fruit_and_country,
            categorical_columns=['country', 'fruit'],
            numeric_column='quantity',
            color_column='country')
        ch.axes.set_xaxis_tick_orientation('vertical')
        ch.show('png')
    



![png](output_19_5.png)


    
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
    



![png](output_19_7.png)


# Interval


```python
print(chartify.examples.plot_interval.__doc__)
chartify.examples.plot_interval()
```

    Interval.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                categorical_columns (str or list): Column name to plot on
                    the categorical axis.
                lower_bound_column (str): Column name to plot on the
                    numerical axis for the lower bound.
                upper_bound_column (str): Column name to plot on the
                    numerical axis for the upper bound.
                middle_column (str, optional): Column name to plot on the
                    numerical axis for the middle tick.
                categorical_order_by (str or array-like, optional):
                    Dimension for ordering the categorical axis. Default 'values'.
                    - 'values': Order categorical axis by the numerical
                        axis values. Default.
                    - 'labels': Order categorical axis by the categorical labels.
                    - array-like object (list, tuple, np.array): New labels
                        to conform the categorical axis to.
                categorical_order_ascending (bool, optional): Sort order of the
                    categorical axis. Default False.
                color (str): Color name or hex value.
                    See chartify.color_palettes.show() for available color names.
            
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
        
    
        avg_price_with_interval = (data.groupby('fruit')['total_price'].agg(
            ['mean', 'std', 'count'])
            .assign(
                lower_ci=lambda x: x['mean'] - 1.96 * x['std'] / x['count']**.5,
                upper_ci=lambda x: x['mean'] + 1.96 * x['std'] / x['count']**.5)
            .reset_index())
        
    
        ch = chartify.Chart(blank_labels=True, x_axis_type='categorical')
        ch.set_title("Interval plots")
        ch.set_subtitle(
            "Represent variation. Optional `middle_column` to mark a middle point."
        )
        ch.plot.interval(
            data_frame=avg_price_with_interval,
            categorical_columns='fruit',
            lower_bound_column='lower_ci',
            upper_bound_column='upper_ci',
            middle_column='mean')
        ch.show('png')
    



![png](output_21_1.png)


    
        ch = chartify.Chart(blank_labels=True, x_axis_type='categorical')
        ch.set_title("Combined interval plot & bar plot")
        ch.plot.bar(
            data_frame=avg_price_with_interval,
            categorical_columns='fruit',
            numeric_column='mean')
        ch.plot.interval(
            data_frame=avg_price_with_interval,
            categorical_columns='fruit',
            lower_bound_column='lower_ci',
            upper_bound_column='upper_ci')
        ch.show('png')
    



![png](output_21_3.png)


## Lollipop


```python
print(chartify.examples.plot_lollipop.__doc__)
chartify.examples.plot_lollipop()
```

    Lollipop chart.
    
            Note:
                To change the orientation set x_axis_type or y_axis_type
                argument of the Chart object.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                categorical_columns (str or list): Column name to plot on
                    the categorical axis.
                numeric_column (str): Column name to plot on the numerical axis.
                color_column (str, optional): Column name to group by on
                    the color dimension.
                color_order (list, optional):
                    List of values within the 'color_column' for
                        specific color sort.
                categorical_order_by (str or array-like, optional):
                    Dimension for ordering the categorical axis. Default 'values'.
                    - 'values': Order categorical axis by the numerical axis values.
                    - 'labels': Order categorical axis by the categorical labels.
                    - array-like object (list, tuple, np.array): New labels
                        to conform the categorical axis to.
                categorical_order_ascending (bool, optional):
                    Sort order of the categorical axis. Default False.
            
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
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
    



![png](output_23_1.png)


## Bar (Stacked)


```python
print(chartify.examples.plot_bar_stacked.__doc__)
chartify.examples.plot_bar_stacked()
```

    Plot stacked bar chart.
    
            Note:
                - To change the orientation set x_axis_type or y_axis_type
                argument of the Chart object.
                - Stacked numeric values must be all positive or all negative.
                To plot both positive and negative values on the same chart
                call this method twice. Once for the positive values and
                once for the negative values.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                categorical_columns (str or list): Column name to plot on
                    the categorical axis.
                numeric_column (str): Column name to plot on the numerical axis.
                stack_column (str): Column name to group by on the stack dimension.
                normalize (bool, optional): Normalize numeric dimension for
                    100% stacked bars. Default False.
                stack_order (list, optional): List of values within the
                    'stack_column' dimension for specific stack sort.
                categorical_order_by (str or array-like, optional):
                    Dimension for ordering the categorical axis. Default 'values'.
                    - 'values': Order categorical axis by the numerical
                        axis values. Default.
                    - 'labels': Order categorical axis by the categorical labels.
                    - array-like object (list, tuple, np.array): New labels
                        to conform the categorical axis to.
                categorical_order_ascending (bool, optional): Sort order
                    of the categorical axis. Default False.
            
    
        import numpy as np
        import pandas as pd
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
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
    



![png](output_25_1.png)


    
        (chartify.Chart(blank_labels=True, x_axis_type='categorical')
         .set_title("Grouped bar chart - Normalized")
         .set_subtitle("Set the 'normalize' parameter for 100% bars.")
         .plot.bar_stacked(
             data_frame=quantity_by_fruit_and_country,
             categorical_columns=['fruit'],
             numeric_column='quantity',
             stack_column='country',
             normalize=True)
         .show('png'))
    



![png](output_25_3.png)


    
        # Get the ordered list of quanity by country to order the stacks.
        country_order = (
            quantity_by_fruit_and_country.groupby('country')['quantity'].sum()
            .sort_values(ascending=False).index)
        (chartify.Chart(blank_labels=True, x_axis_type='categorical')
         .set_title("Grouped bar chart - Ordered stack")
         .set_subtitle("Change the order of the stack with `stack_order`.")
         .plot.bar_stacked(
             data_frame=quantity_by_fruit_and_country,
             categorical_columns=['fruit'],
             numeric_column='quantity',
             stack_column='country',
             normalize=True,
             stack_order=country_order)
         .show('png'))
        



![png](output_25_5.png)


    
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
    



![png](output_25_7.png)


# Parallel coordinate plot


```python
print(chartify.examples.plot_parallel.__doc__)
chartify.examples.plot_parallel()
```

    Parallel coordinate plot.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                categorical_columns (str or list): Column name to plot on
                    the categorical axis.
                numeric_column (str): Column name to plot on the numerical axis.
                color_column (str, optional): Column name to group by on
                    the color dimension.
                color_order (list, optional): List of values within the
                    'color_column' for specific color sort.
                categorical_order_by (str or array-like, optional):
                    Dimension for ordering the categorical axis. Default 'values'.
                    - 'values': Order categorical axis by the numerical axis values.
                    - 'labels': Order categorical axis by the categorical labels.
                    - array-like object (list, tuple, np.array): New labels
                        to conform the categorical axis to.
                categorical_order_ascending (bool, optional):
                    Sort order of the categorical axis. Default False.
                line_dash (str, optional): Dash style for the line. One of:
                    - 'solid'
                    - 'dashed'
                    - 'dotted'
                    - 'dotdash'
                    - 'dashdot'
                line_width (int, optional): Width of the line
                alpha (float): Alpha value
            
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
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
    



![png](output_27_1.png)



```python
print(chartify.examples.plot_scatter_categorical.__doc__)
chartify.examples.plot_scatter_categorical()
```

    Scatter chart.
    
            Note:
                To change the orientation set x_axis_type or y_axis_type
                argument of the Chart object.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                categorical_columns (str or list): Column name to plot on
                    the categorical axis.
                numeric_column (str): Column name to plot on the numerical axis.
                size_column (str, optional): Column name of numerical values
                    to plot on the size dimension.
                color_column (str, optional): Column name to group by on
                    the color dimension.
                color_order (list, optional):
                    List of values within the 'color_column' for
                        specific color sort.
                categorical_order_by (str or array-like, optional):
                    Dimension for ordering the categorical axis. Default 'count'.
                    - 'count': Order categorical axis by the count of values.
                    - 'labels': Order categorical axis by the categorical labels.
                    - array-like object (list, tuple, np.array): New labels
                        to conform the categorical axis to.
                categorical_order_ascending (bool, optional):
                    Sort order of the categorical axis. Default False.
                alpha (float): Alpha value.
                marker (str): marker type. Valid types:
                    'asterisk', 'circle', 'circle_cross', 'circle_x', 'cross',
                    'diamond', 'diamond_cross', 'hex', 'inverted_triangle',
                    'square', 'square_x', 'square_cross', 'triangle',
                    'x', '*', '+', 'o', 'ox', 'o+'
            
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
        high_low = (data.groupby(['fruit'])['unit_price']
                    .agg(['max', 'min'])
                    .reset_index())
        print(high_low.head())
        
        fruit       max       min
    0   Apple  1.244992  0.767347
    1  Banana  0.326851  0.171751
    2   Grape  2.516920  1.433120
    3  Orange  0.632614  0.355687
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True,
                            y_axis_type='categorical')
        ch.set_title("Scatter plot with categorical y-axis")
        ch.plot.scatter(
            data_frame=high_low,
            categorical_columns='fruit',
            numeric_column='max',
            marker='circle',
        )
        ch.plot.scatter(
            data_frame=high_low,
            categorical_columns='fruit',
            numeric_column='min',
            marker='square',
        )
        ch.show('png')
    



![png](output_28_1.png)


# Both categorical axes

## Heatmap


```python
print(chartify.examples.plot_heatmap.__doc__)
chartify.examples.plot_heatmap()
```

    Heatmap.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                x_column (str): Column name to plot on the x axis.
                y_column (str): Column name to plot on the y axis.
                color_column (str): Column name of numerical type to plot on
                    the color dimension.
                text_column (str or None): Column name of the text labels.
                color_palette (str, chartify.ColorPalette): Color palette to
                    apply to the heatmap.
                    See chartify.color_palettes.show() for available color palettes.
                reverse_color_order (bool): Reverse order of the color palette.
                text_color (str): Color name or hex value.
                    See chartify.color_palettes.show() for available color names.
                text_format: Python string formatting to apply to the text labels.
                color_value_min (float): Minimum value for the color palette.
                    If None, will default to the min value of the
                    color_column dimension.
                color_value_max (float): Maximum value for the color palette.
                    If None, will default to the max value of the
                    color_column dimension.
                color_value_range (int): The size of the range of colors in
                    the color palette.
                    A larger color range will result in greater variation
                    among the cell colors.
                
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        average_price_by_fruit_and_country = (data.groupby(
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
    



![png](output_31_1.png)


# Single density axis


```python
print(chartify.examples.plot_histogram.__doc__)
chartify.examples.plot_histogram()
```

    Kernel Density Estimate Plot.
    
            Args:
                data_frame (pandas.DataFrame): Data source for the plot.
                values_column (str): Column of numeric values.
                color_column (str, optional): Column name to group by on
                    the color dimension.
                color_order (list, optional): List of values within the
                    'color_column' for specific sorting of the colors.
            
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        print(data.head())
        
            date country   fruit  unit_price  quantity  total_price
    0 2017-10-21      US  Banana    0.303711         4     1.214846
    1 2017-05-30      JP  Banana    0.254109         4     1.016436
    2 2017-05-21      CA  Banana    0.268635         4     1.074539
    3 2017-09-18      BR   Grape    2.215277         2     4.430554
    4 2017-12-08      US  Banana    0.308337         5     1.541687
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True, y_axis_type='density')
        ch.set_title("Histogram")
        ch.set_subtitle("")
        ch.plot.histogram(
            data_frame=data,
            values_column='unit_price',
            bins=50)
        ch.show('png')
    



![png](output_33_1.png)


    
        ch = chartify.Chart(blank_labels=True, x_axis_type='density')
        ch.set_title("Horizontal histogram with grouping")
        ch.set_subtitle("")
        ch.plot.histogram(
            data_frame=data,
            values_column='unit_price',
            color_column='fruit')
        ch.show('png')
    



![png](output_33_3.png)



```python
print(chartify.examples.plot_kde.__doc__)
chartify.examples.plot_kde()
```

    
        KDE example
        
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        print(data.head())
        
            date country   fruit  unit_price  quantity  total_price
    0 2017-10-21      US  Banana    0.303711         4     1.214846
    1 2017-05-30      JP  Banana    0.254109         4     1.016436
    2 2017-05-21      CA  Banana    0.268635         4     1.074539
    3 2017-09-18      BR   Grape    2.215277         2     4.430554
    4 2017-12-08      US  Banana    0.308337         5     1.541687
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True, y_axis_type='density')
        ch.set_title("KDE plot")
        ch.plot.kde(
            data_frame=data,
            values_column='unit_price',
            color_column='fruit')
        ch.show('png')
    



![png](output_34_1.png)


    
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
    



![png](output_34_3.png)


# Both density axes


```python
print(chartify.examples.plot_hexbin.__doc__)
chartify.examples.plot_hexbin()
```

    
        Hexbin example
        
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        ch = chartify.Chart(blank_labels=True,
                            x_axis_type='density',
                            y_axis_type='density')
        ch.set_title("Hexbin")
        ch.plot.hexbin(data_frame=data,
                       x_values_column='unit_price',
                       y_values_column='quantity',
                       size=.2,
                       orientation='pointytop')
        ch.show('png')
    



![png](output_36_1.png)


# Second Y axis


```python
chartify.examples.chart_second_axis()
```

    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        # Sum price grouped by date
        price_by_date = (
            data.groupby('date')['total_price'].sum()
            .reset_index()  # Move 'date' from index to column
            )
        price_by_date['triple_total_price'] = price_by_date['total_price'] * 3
        price_by_date = price_by_date.sort_values('date')
        print(price_by_date.head())
        
            date  total_price  triple_total_price
    0 2017-01-10     1.808778            5.426334
    1 2017-01-12     0.829621            2.488864
    2 2017-01-22     1.998476            5.995427
    3 2017-01-27     1.390764            4.172292
    4 2017-01-28     2.658465            7.975394
    
        # Initialize chart with second_y_axis=True
        ch = chartify.Chart(blank_labels=True,
                            x_axis_type='datetime',
                            y_axis_type='linear',
                            second_y_axis=True)
        ch.set_title("Second Y axis")
        # Plot the first axis
        ch.plot.line(
            data_frame=price_by_date,
            x_column='date',
            y_column='total_price')
        ch.axes.set_yaxis_range(0, 50)
        ch.axes.set_yaxis_label('First axis label')
        ch.axes.set_yaxis_tick_format('0a')
    
        # Plot the second axis
        ch.second_axis.axes.set_yaxis_range(0, 80)
        ch.second_axis.axes.set_yaxis_label('Second axis label')
        ch.second_axis.plot.line(
            # Data must be sorted by x column
            data_frame=price_by_date,
            x_column='date',
            y_column='triple_total_price')
        ch.second_axis.axes.set_yaxis_tick_format('0.0')
        ch.show('png')
    



![png](output_38_1.png)


# Radar chart


```python
chartify.examples.plot_radar_area()
```

    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
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
    



![png](output_40_1.png)



```python
chartify.examples.plot_radar_radius()
```

    
        import chartify
        from itertools import product
        # Generate example data
        data = chartify.examples.example_data()
    
        total_by_country = data.groupby(['country'])['quantity'].sum().reset_index()
        countries = total_by_country.country.unique()
        grid_values = product(range(0, 1200, 200), countries)
        grid_df = pd.DataFrame.from_records(grid_values, columns=['quantity', 'country'])
        quantity_label = grid_df.groupby('quantity')[['quantity']].min().reset_index(drop=True)
    
        ch = chartify.RadarChart(True, layout='slide_50%')
        ch.set_title('Radar Radius Chart')
    
        ch.style.set_color_palette('categorical', ['grey'])
        # Plot quantity labels
        ch.plot.text(quantity_label,
                     'quantity',
                     text_column='quantity',
                     color_column='quantity',
                     font_size='8pt')
        # Plot perimeter grid
        ch.plot.perimeter(grid_df,
                          radius_column='quantity',
                          color_column='quantity',
                          line_width=1)
        ch.style.set_color_palette('categorical')
    
        # Plot text labels
        ch.plot.text(total_by_country,
                     'quantity',
                     text_column='country',
                     text_align='center')
        ch.style.color_palette.reset_palette_order()
        # Plot the radius
        ch.plot.radius(total_by_country, 'quantity')
        ch.axes.hide_yaxis()
        ch.axes.hide_xaxis()
        ch.set_legend_location(None)
        ch.show('png')
    



![png](output_41_1.png)


# Chart aesthetics

## Labels


```python
print(chartify.examples.chart_labels.__doc__)
chartify.examples.chart_labels()
```

    
        Chart label examples
        
    
        import numpy as np
        import pandas as pd
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        apple_prices = (data[data['fruit'] == 'Apple']
                        .groupby(['quantity'])['unit_price'].mean().reset_index())
        # Plot the data with method chaining
        (chartify.Chart(blank_labels=True)
         .plot.scatter(apple_prices, 'quantity', 'unit_price')
         .set_title(
             "Quantity decreases as price increases. <--  Use title for takeaway.")
         .set_subtitle(
             "Quantity vs. Price. <-- Use subtitle for data description.")
         .axes.set_xaxis_label("Quantity per sale (Apples)")
         .axes.set_yaxis_label("Price ($)")
         .axes.set_yaxis_tick_format("$0.00")
         .show('png'))
    



![png](output_44_1.png)


# Axis type



```python
print(chartify.examples.axes_axis_type.__doc__)
chartify.examples.axes_axis_type()
```

    
        Axis type examples
        
    
        import numpy as np
        import pandas as pd
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        # Plot the data
        (chartify.Chart(blank_labels=True, x_axis_type='log')
         .plot.scatter(
            data_frame=data,
            x_column='total_price',
            y_column='quantity')
         .set_subtitle(
            "Set axis type for auto handling of categorical, datetime, linear, or log values."
        )
         .set_title("Axis Type")
         .show('png'))
    



![png](output_46_1.png)


# Tick label format


```python
chartify.examples.axes_axis_tick_format()
```

    
        import numpy as np
        import pandas as pd
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
        data['%_sales'] = data['quantity'] / data['quantity'].sum()
    
        # Plot the data
        (chartify.Chart(blank_labels=True)
         .plot.scatter(
            data_frame=data,
            x_column='%_sales',
            y_column='unit_price')
         .axes.set_yaxis_tick_format("$0.00")
         .axes.set_xaxis_tick_format("0.00%")
         .set_subtitle("Format ticks on either axis to set units or precision")
         .set_title("Axis tick format").show('png'))
    



![png](output_48_1.png)


# Axis tick values


```python
chartify.examples.axes_axis_tick_values()
```

    
        import pandas as pd
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
        ch.plot.scatter(data, 'date', 'quantity')
        ch.set_title("Axis tick values")
        ch.set_subtitle(
            "Pass a list of values or use pd.date_range for datetime axes")
        # Use pd.date_range to generate a range of dates
        # at the start of each month
        ch.axes.set_xaxis_tick_values(
            pd.date_range('2017-01-01', '2018-01-01', freq='MS'))
        ch.axes.set_yaxis_tick_values(list(range(0, 8, 2)))
        ch.show('png')
    



![png](output_50_1.png)


# Callouts

## Line callout


```python
print(chartify.examples.callout_line.__doc__)
chartify.examples.callout_line()
```

    
        Line example
        
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        # Plot the data
        (chartify.Chart(blank_labels=True)
         .plot.scatter(
            data_frame=data,
            x_column='unit_price',
            y_column='total_price')
         .callout.line(2)  # Callout horizontal line
         .callout.line(1, 'height')  # Callout vertical line
         .set_title('Line callout')
         .set_subtitle("Callout lines on either axis")
         .show('png'))
    



![png](output_53_1.png)


## Box callout


```python
print(chartify.examples.callout_box.__doc__)
chartify.examples.callout_box()
```

    Add box callout to the chart.
    
            Args:
                top (numeric, optional): Top edge of the box.
                bottom (numeric, optional): Bottom edge of the box.
                left (numeric, optional): Left edge of the box.
                right (numeric, optional): Right edge of the box.
                alpha (float, optional): 0.2
                color (str): Color name or hex value.
                    See chartify.color_palettes.show() for available color names.
    
            Note:
                The box will extend to the edge if the corresponding position
                argument is omitted.
    
            Returns:
                Current chart object
            
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        # Plot the data
        (chartify.Chart(blank_labels=True)
         .plot.scatter(
            data_frame=data,
            x_column='total_price',
            y_column='unit_price')
         .callout.box(top=1, bottom=-1, color='red')
         .callout.box(top=2, left=4, color='blue')
         .callout.box(bottom=2, right=3, color='green')
         .set_title("Shaded area callout")
         .set_subtitle("Highlight notable areas of your chart")
         .show('png'))
    



![png](output_55_1.png)


## Text callout


```python
print(chartify.examples.callout_text.__doc__)
chartify.examples.callout_text()
```

    Add text callout to the chart.
    
            Note:
                Use `
    ` within text for newlines.
            Args:
                x (numeric): x location of the text.
                y (numeric, optional): y location of the text.
                text_color (str): Color name or hex value.
                    See chartify.color_palettes.show() for available color names.
                text_align (str: 'left', 'right', 'center'): Text alignment.
                font_size (str): Font size.
                angle (int, 0 to 360): Angle in degrees from horizontal. Default: 0
    
            Returns:
                Current chart object
            
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True)
        ch.plot.scatter(
            data_frame=data,
            x_column='unit_price',
            y_column='total_price')
        ch.callout.text("Description of what is\ngoing on in this chart!", 0, 6)
        ch.set_title("Text callout")
        ch.set_subtitle("Add narrative to your chart.")
        ch.show('png')
    



![png](output_57_1.png)


# Color Palettes


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



## Categorical


```python
print(chartify.examples.style_color_palette_categorical.__doc__)
chartify.examples.style_color_palette_categorical()
```

    
        Color palette
        
    
        import numpy as np
        import pandas as pd
        import chartify
    
        # Generate example data
        data = pd.DataFrame({'x': list(range(100))})
        data['y'] = data['x'] * np.random.normal(size=100)
        data['z'] = np.random.choice([2, 4, 5], size=100)
        data['country'] = np.random.choice(
            ['US', 'GB', 'CA', 'JP', 'BR'], size=100)
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True)
        ch.style.set_color_palette(palette_type='categorical')
        ch.plot.scatter(
            data_frame=data,
            x_column='x',
            y_column='y',
            color_column='country')
        ch.set_title("Categorical color palette type")
        ch.set_subtitle(
            "Default palette type. Use to differentiate categorical series.")
        ch.show('png')
        



![png](output_62_1.png)


    
        # Plot the data
        ch = chartify.Chart(blank_labels=True)
        ch.style.set_color_palette(
            palette_type='categorical',)
        ch.plot.scatter(
            data_frame=data,
            x_column='x',
            y_column='y',
            color_column='country')
        ch.set_title(
            "Pass 'palette' parameter to .set_color_palette() to change palette colors."
        )
        ch.set_subtitle("")
        ch.show('png')
    



![png](output_62_3.png)


# Accent


```python
print(chartify.examples.style_color_palette_accent.__doc__)
chartify.examples.style_color_palette_accent()
```

    
        Color palette
        
    
        import numpy as np
        import pandas as pd
        import chartify
    
        # Generate example data
        data = pd.DataFrame({'x': list(range(100))})
        data['y'] = data['x'] * np.random.normal(size=100)
        data['z'] = np.random.choice([2, 4, 5], size=100)
        data['country'] = np.random.choice(
            ['US', 'GB', 'CA', 'JP', 'BR'], size=100)
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True)
        ch.style.set_color_palette('accent', accent_values=['US', 'CA'])
        ch.plot.scatter(
            data_frame=data,
            x_column='x',
            y_column='y',
            size_column='z',
            color_column='country')
        ch.set_title("Accent color palette")
        ch.set_subtitle(
            "Highlight specific color values or assign specific colors to values.")
        ch.show('png')
    



![png](output_64_1.png)


# Sequential


```python
print(chartify.examples.style_color_palette_sequential.__doc__)
chartify.examples.style_color_palette_sequential()
```

    
        Color palette sequential
        
    
        import numpy as np
        import pandas as pd
        import chartify
    
        data = pd.DataFrame({'time': pd.date_range('2015-01-01', '2018-01-01')})
        n_days = len(data)
        data['1st'] = np.array(list(range(n_days))) + np.random.normal(
            0, 10, size=n_days)
        data['2nd'] = np.array(list(range(n_days))) + np.random.normal(
            0, 10, size=n_days) + 200
        data['3rd'] = np.array(list(range(n_days))) + np.random.normal(
            0, 10, size=n_days) + 500
        data['4th'] = np.array(list(range(n_days))) + np.random.normal(
            0, 10, size=n_days) + 700
        data['5th'] = np.array(list(range(n_days))) + np.random.normal(
            0, 10, size=n_days) + 800
        data['6th'] = np.array(list(range(n_days))) + np.random.normal(
            0, 10, size=n_days) + 1000
        data = pd.melt(
            data,
            id_vars=['time'],
            value_vars=data.columns[1:],
            value_name='y',
            var_name=['grouping'])
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
        ch.style.set_color_palette(palette_type='sequential')
        ch.plot.line(
            data_frame=data.sort_values('time'),
            x_column='time',
            y_column='y',
            color_column='grouping')
        ch.set_title("Sequential color palette type")
        ch.set_subtitle("Palette type for sequential ordered dimensions")
        ch.show('png')
    



![png](output_66_1.png)


# Diverging


```python
print(chartify.examples.style_color_palette_diverging.__doc__)
chartify.examples.style_color_palette_diverging()
```

    
        Color palette sequential
        
    
        import numpy as np
        import pandas as pd
        import chartify
    
        data = pd.DataFrame({'time': pd.date_range('2015-01-01', '2018-01-01')})
        n_days = len(data)
        data['Very Unlikely'] = np.array(list(range(n_days))) + np.random.normal(
            0, 10, size=n_days)
        data['Unlikely'] = np.array(list(range(n_days))) + np.random.normal(
            0, 10, size=n_days) + 200
        data['Neutral'] = np.array(list(range(n_days))) + np.random.normal(
            0, 10, size=n_days) + 500
        data['Likely'] = np.array(list(range(n_days))) + np.random.normal(
            0, 10, size=n_days) + 700
        data['Very Likely'] = np.array(list(range(n_days))) + np.random.normal(
            0, 10, size=n_days) + 800
        data = pd.melt(
            data,
            id_vars=['time'],
            value_vars=data.columns[1:],
            value_name='y',
            var_name=['grouping'])
    
        # Plot the data
    
        ch = chartify.Chart(blank_labels=True, x_axis_type='datetime')
        ch.style.set_color_palette(palette_type='diverging')
        color_order = [
            'Very Unlikely', 'Unlikely', 'Neutral', 'Likely', 'Very Likely'
        ]
        ch.plot.line(
            data_frame=data.sort_values('time'),
            x_column='time',
            y_column='y',
            color_column='grouping',
            color_order=color_order)  # Your data must be sorted
        ch.set_title("Diverging color palette type")
        ch.set_subtitle("Palette type for diverging ordered dimensions")
        ch.show('png')
    



![png](output_68_1.png)



```python
print(chartify.examples.style_color_palette_custom.__doc__)
chartify.examples.style_color_palette_custom()
```

    
        Custom color palette
        
    
        import chartify
    
        # Generate example data
        data = chartify.examples.example_data()
    
        # Create a new custom palette
        chartify.color_palettes.create_palette(colors=['#ff0000', 'yellow',
                                                       'purple', 'orange'],
                                               palette_type='categorical',
                                               name='custom palette')
    
        ch = chartify.Chart(blank_labels=True)
        # Apply the custom palette
        ch.style.set_color_palette('categorical', 'custom palette')
        ch.plot.scatter(
            data_frame=data,
            x_column='unit_price',
            y_column='quantity',
            color_column='fruit')
        ch.set_title("Custom color palette")
        ch.show('png')
    



![png](output_69_1.png)


# Layouts


```python
chartify.examples.chart_layouts()
```

    
        import numpy as np
        import pandas as pd
        import chartify
    
        # Generate example data
        data = pd.DataFrame({'Price': list(range(100))})
        data['Demand'] = 100 + -.5 * data['Price'] + np.random.normal(size=100)
    
        layouts = ['slide_100%', 'slide_75%', 'slide_50%', 'slide_25%']
    
        def display_layout(layout):
            (chartify.Chart(
                layout=layout)  # Assign the layout when instantiating the chart.
             .plot.scatter(
                data_frame=data,
                x_column='Price',
                y_column='Demand')
             .set_title("Slide layout: '{}'".format(layout))
             .set_subtitle("Demand vs. Price.")
             .set_source_label("")
             .axes.set_xaxis_label("Demand (# Users)")
             .axes.set_yaxis_label("Price ($)")
             .show('png'))
    
        [display_layout(layout) for layout in layouts]
    



![png](output_71_1.png)



![png](output_71_2.png)



![png](output_71_3.png)



![png](output_71_4.png)


# Show Chart


```python
print(chartify.examples.chart_show.__doc__)
chartify.examples.chart_show()
```

    Show the chart.
    
            Args:
                format (str):
                    - 'html': Output chart as HTML.
                        Renders faster and allows for interactivity.
                        Charts saved as HTML in a Jupyter notebooks
                        WILL NOT display on Github.
                        Logos will not display on HTML charts.
                        Recommended when drafting plots.
    
                    - 'png': Output chart as PNG.
                        Easy to copy+paste into slides.
                        Will render logos.
                        Recommended when the plot is in a finished state.
    
                    - 'svg': Output as SVG.
                    
    
        import numpy as np
        import pandas as pd
        import chartify
    
        # Generate example data
        data = pd.DataFrame({'x': list(range(100))})
        data['y'] = data['x'] * np.random.normal(size=100)
        data['z'] = np.random.choice([2, 4, 5], size=100)
        data['country'] = np.random.choice(
            ['US', 'GB', 'CA', 'JP', 'BR'], size=100)
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True)
        ch.plot.scatter(
            data_frame=data,
            x_column='x',
            y_column='y',
            size_column='z',
            color_column='country')
        ch.set_title(
            'ch.show(): Faster rendering with HTML. Recommended while drafting.')
        ch.set_subtitle('No watermark. Does not display on github.')
        ch.show('html')  # Show with HTML
    
        ch.set_title(
            'ch.show("png"): Return a png file for easy copying into slides')
        ch.set_subtitle('Will display on github.')
        ch.show('png')  # Show with PNG
    









<div class="bk-root" id="6be3f7e2-4e76-4d39-ae28-f7590c459598"></div>






![png](output_73_3.png)


# Save Chart


```python
print(chartify.examples.chart_save.__doc__)
chartify.examples.chart_save()
```

    Save the chart.
    
            Args:
                filename (str): Name of output file.
                format (str):
                    - 'html': Output chart as HTML.
                        Renders faster and allows for interactivity.
                        Charts saved as HTML in a Jupyter notebook WILL NOT display
                        on Github.
                        Logos will not display on HTML charts.
                        Recommended when drafting plots.
    
                    - 'png': Output chart as PNG.
                        Easy to paste into google slides.
                        Recommended when the plot is in a finished state.
                        Will render logos.
    
                    - 'svg': Output as SVG.
            
    
        import chartify
    
        # Plot the data
        ch = chartify.Chart(blank_labels=True)
        ch.set_title(
            'ch.show(): Save chart to html, png, or svg.')
        ch.save('saved_chart_example.html', format='html')  # Save to html
    
    Saved to saved_chart_example.html

