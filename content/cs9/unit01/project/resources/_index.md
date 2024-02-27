---
Title: "[Tips & Tricks]"
# draft: true
---

# Tips & Tricks

This page will be home to helpful tips and tricks of `Pandas`. Think of these resources as as an FAQs (frequently asks questions).


*Feel free to let a teacher know if you have any suggestions of what we should add.*

---

## Creating a New Column Based on Another Columns


📖 **Here is a `dataframe` stored in the variable `age_df`.** It stores names and ages.


|   | name    | age |
|---|---------|-----|
| 0 | Alice   | 10  |
| 1 | Bob     | 15  |
| 2 | Charlie | 25  |
| 3 | David   | 40  |
| 4 | Sally   | 80  |


📖 **In one code block, you will write a function with your conditional statements.** This function returns `True` or `False`, based on their age. 

```python
def get_if_adult(age):
    if age < 18:
        return False
    else:
        return True
```

📖 **In another code block, you can apply the function to each value in a given row.** Here it applies the function `get_if_adult()` to each row of the `age` columns, and stores the return value in a new column called `is_adult`.
```python
# Apply the get_age_group function to the age column
age_df['is_adult']  = age_df.apply(lambda row: get_if_adult(row['age']), axis=1)
```
📖 **Here is the updated dataframe.**

|   | name    | age | is_adult |
|---|---------|-----|----------|
| 0 | Alice   | 10  | False    |
| 1 | Bob     | 15  | False    |
| 2 | Charlie | 25  | True     |
| 3 | David   | 40  | True     |
| 4 | Sally   | 80  | True     |

*This tutorial is based of [this](https://saturncloud.io/blog/how-to-create-a-new-column-based-on-the-value-of-another-column-in-pandas/#:~:text=Once%20we%20have%20had%20our,and%20return%20a%20new%20DataFrame.) guide.*


---

## Find the top 1 (or 5) based on two columns

For example, I want to find the top 1 show I watched each month.

📖 **Here is a `dataframe` stored in the variable `watch_history_df`.** 


|   | month    | show       | episode | genre     |
|---|----------|------------|---------|-----------|
| 0 | January  | One Piece  | 08      | Fantasy   |
| 1 | January  | One Piece  | 09      | Fantasy   |
| 2 | January  | The Office | 15      | Comedy    |
| 3 | February | Avatar     | 01      | Animation |
| 4 | February | Avatar     | 02      | Animation |
| 5 | February | Avatar     | 03      | Animation |


1️⃣ **Count how many times we watched each `show` during each `month`.** For this we must use `groupby`.

```python
#this counts up how many times I watched each show in each month
top_show_df = watch_history_df.groupby(by=["month", "show"]).size().to_frame("count")
```

2️⃣ **Next, sort the values.** Sort by month, then the count. We use ascending for the month, since we want to start with the lowest number (1 for january). We use descending for count, since we want the most watched at the top.

```python
#this sorts the new df first by month, then by the count
top_show_df = top_show_df.sort_values(['month', 'count'], ascending=[True, False])
```

3️⃣ **Last, get the top 1 show for each month.** To do this, we use `groupby` combined with `head`. If you want the top 3, you could use `.head(3)`, etc.

```python
#this gets the top 1 for every month
top_show_df = top_show_df.groupby('month').head(1)
```

📖 **Here is the new dataframe `top_show_df`.**

| month | show      | count |
|-------|-----------|-------|
| 1     | One Piece | 2     |
| 2     | Avatar    | 3     |


---
## Find the mode of a column for each unique value in another column 

📖 **Here is a `dataframe` stored in the variable `age_df`.** It stores names, ages, is_adult, and house.

```python
age_df.head()
```

|   | name    | age | is_adult | house   |
|---|---------|-----|----------|---------|
| 0 | Alice   | 10  | False    | 'fire'  |
| 1 | Bob     | 15  | False    | 'metal' |
| 2 | Charlie | 25  | True     | 'metal' |
| 3 | David   | 40  | True     | 'fire'  |
| 4 | Sally   | 80  | True     | 'fire   |

📖 **We want to see what is the `mode` of `is_adult` for each `house`.** For this we must use `groupby`. 

```python
mode_isAdult_by_house_df =  age_df.groupby(['house'])['is_adult'].agg(pd.Series.mode).to_frame().reset_index()
```

📖 **Here is the new dataframe `mode_isAdult_by_house_df`.**
> For `metal`, because `True` and `False` appear the same amount of times it returns both options. 

```python
mode_isAdult_by_house_df
```

|   | house | is_adult         |
|---|-------|------------------|
| 0 | fire  | True             |
| 1 | metal | ['False','True'] |

*This tutorial is based of [this](https://stackoverflow.com/questions/15222754/groupby-pandas-dataframe-and-select-most-common-value) post.*

---


## Find the mean of a column for each unique value in another column 

📖 **Here is a `dataframe` stored in the variable `age_df`.** It stores names, ages, is_adult, and house.

```python
age_df.head()
```

|   | name    | age | is_adult | house   |
|---|---------|-----|----------|---------|
| 0 | Alice   | 10  | False    | 'fire'  |
| 1 | Bob     | 15  | False    | 'metal' |
| 2 | Charlie | 25  | True     | 'metal' |
| 3 | David   | 40  | True     | 'fire'  |
| 4 | Sally   | 80  | True     | 'fire   |

📖 **We want to see what is the `mean` of `is_adult` for each `age`.** For this we must use `groupby`. 
> You could also replace `.mean()` with `.max()` or `.min()`
>
> To round the mean, add `.round(3)` after `.mean()`

```python
mean_isAdult_by_age_df =  df.groupby(['is_adult'])['age'].mean().to_frame().reset_index()
```

📖 **Here is the new dataframe `mean_isAdult_by_age_df`.**


```python
mode_isAdult_by_house_df
```

|   | is_adult | age       |
|---|----------|-----------|
| 0 | True     | 27.500000 |
| 1 | False    | 47.333333 |

---

## Compare a value to the value right above it


📖 **Here is a `dataframe` stored in the variable `watch_history_df`.** It stores shows, episodes, and genre.

```python
watch_history_df.head()
```

|   | show       | episode | genre     |
|---|------------|---------|-----------|
| 0 | One Piece  | 08      | Fantasy   |
| 1 | One Piece  | 09      | Fantasy   |
| 2 | The Office | 15      | Comedy    |
| 3 | Avatar     | 01      | Animation |
| 4 | Avatar     | 02      | Animation |
| 5 | Avatar     | 03      | Animation |

📖 **We want to add a column to see what the previous show was called.** For this we must use `shift`.

> You could also put a number in the brackets to shift more than just 1 row down
>
> For example, `.shift(2)` or `.shift(-1)`


```python
watch_history_df['previous'] = watch_history_df['show'].shift()
watch_history_df.head()
```

|   | show       | episode | genre     | previous   |
|---|------------|---------|-----------|------------|
| 0 | One Piece  | 08      | Fantasy   | None       |
| 1 | One Piece  | 09      | Fantasy   | One Piece  |
| 2 | The Office | 15      | Comedy    | One Piece  |
| 3 | Avatar     | 01      | Animation | The Office |
| 4 | Avatar     | 02      | Animation | Avatar     |
| 5 | Avatar     | 03      | Animation | Avatar     |

📖 **Now we will add a new column to track if the show is the same as the previous one.**

```python
watch_history_df["repeat"] = watch_history_df["show"] == watch_history_df["previous"]
watch_history_df.head()
```

|   | show       | episode | genre     | previous   | repeat |
|---|------------|---------|-----------|------------|--------|
| 0 | One Piece  | 08      | Fantasy   | None       | False  |
| 1 | One Piece  | 09      | Fantasy   | One Piece  | True   |
| 2 | The Office | 15      | Comedy    | One Piece  | False  |
| 3 | Avatar     | 01      | Animation | The Office | False  |
| 4 | Avatar     | 02      | Animation | Avatar     | True   |
| 5 | Avatar     | 03      | Animation | Avatar     | True   |
---

## Grouped Bar Chart

**A grouped bar chart allows you to compare multiple sets of similar data.**

📖 **In this chart, we compare two people and their number of cats and dogs.** Their data is stored in `person1df` and `person2df`. The dataframes are identical, except for the `count` column.


```python
person1df         
```
|   | animal | count |
|---|--------|-------|
| 0 | dog    | 25    |
| 1 | cat    | 30    |

```python
person2df         
```
|   | animal | count |
|---|--------|-------|
| 0 | dog    | 50    |
| 1 | cat    | 23    |

📖  **This is how you create a group bar chart with two dataframes.**

```python
fig = go.Figure(data=[
    go.Bar(name='person a', x=person1df.animal, y=person1df.count, text=df1.Name),
    go.Bar(name='person b', x=person2df.animal, y=person2df.count, text=df2.Name)
])


fig.update_layout(
    barmode='group',
    title="Plot Title",
    xaxis_title="x axis title",
    yaxis_title="y axis title",
    )

fig.show()
```

{{< figure src="images/courses/cs9/unit01/resouces_groupedbar.png" width="100%" >}}

---

## Line Charts with Multiple Lines

**A grouped bar chart allows you to compare multiple sets of similar data.**

📖 **In this chart, we compare two people and their heights over 5 years.** Their data is stored in `person1df` and `person2df`. The dataframes are identical, except for the `count` column.


```python
person1df         
```
|   | year | height |
|---|------|--------|
| 0 | 2020 | 150    |
| 1 | 2021 | 155    |
| 1 | 2022 | 160    |
| 1 | 2023 | 164    |
| 1 | 2024 | 165    |

```python
person2df          
```
|   | year | height |
|---|------|--------|
| 0 | 2020 | 165    |
| 1 | 2021 | 168    |
| 1 | 2022 | 170    |
| 1 | 2023 | 173    |
| 1 | 2024 | 175    |

📖  **This is how you create a group bar chart with two dataframes.**

```python
fig = go.Figure()

fig.add_trace(go.Scatter(x=person1df.year, y=person1df.height, name='person 1'))

fig.add_trace(go.Scatter(x=person2df.year, y=person2df.height, name='person 2'))

fig.update_xaxes(type='category') # only exisiting values for ticks 

fig.update_layout(
    title="Plot Title",
    xaxis_title="height",
    yaxis_title="years",
    )

fig.show()
```

{{< figure src="images/courses/cs9/unit01/resouces_linechart.png" width="100%" >}}



<!-- ## Creating a Frequency Table and Graph

When analyzing a CSV of our media history, we'll often see duplicates.

Consider this `.csv` file with Netflix data:
> The columns are `tv_show_title` and `season`
>
> Each row is an episode of TV watched.
```shell
tv_show_title,          season,     
Brooklyn Nine-Nine,     Season 1
Brooklyn Nine-Nine,     Season 1
Brooklyn Nine-Nine,     Season 1
Friends,                Season 2
Friends,                Season 1
Community,              Season 1
Community,              Season 1
```

If we use `.count()` to find the total number of rows in the `tv_show_title` column this will *not* give us an accurate number of unique tv shows watched. This will simply give us the total number of episodes of tv shows watched.

**To find the number of unique tv shows watched, we can create a new frequency table in a pandas `series`.**



```python3
frequency_series = df['tv_show_title'].value_counts()
frequency_series
```

> ```
> Brooklyn Nine-Nine    118
> Friends                50
> Community              48
> Gilmore Girls          45
> Queer Eye              32
> Name: tv_show_title, Length: 5, dtype: int64
> ```

**To access just the tv shows, we can use `.index` to get a list of the tv show titles**

```python3
frequency_series.index
```

> ```
> Index(['Brooklyn Nine-Nine', 'Friends', 'Community', 'Gilmore Girls',
>        'Queer Eye'],
>       dtype='object')
> ```

**To access just the frequency values, we can use `.values` to get a list of the number of times each show was watched.**
```python3
frequency_series.values
```

> ```
> array([118,  50,  48,  45,  32])
> ```

**We can then use `MatPlotLib` to create a bar chart.**

```python3
# Using the frequency_series, we can great a bar graph.
plt.bar(frequency_series.index,frequency_series.values)

# Adds a label to the x-axis
plt.xlabel('TV Shows')

# Adds a title to the y-axis
plt.ylabel('Amount Watched')

# To add a title to the plot
plt.title('Relationship between TV Show and Number of Episodes Watched')

# Displays Plot
plt.show()
```

{{< figure src="images/courses/cs9/unit01/resources_01.png" width="100%" >}}

---
## Spotify Genres

Interacting with the genres column of your spotify data can be tricky, because although this data looks like a list, it is really a string. You'll need to convert it from a string to a list. The following code is an example of how you can collect all of the genres from a particular dataframe into a list.

**Feel free to copy/paste it to use in your code:**

```python
genre_data = df['genres'] #get the genres column
all_genres = [] #create an empty list to store the genres
for genre_list in genre_data: #iterate through each row
    for genre in genre_list.strip('][').split(', '): #convert the string to a list, then iterate through each genre in the list
        all_genres.append(genre) #add the genre to our new list
```
If you want to know how many time each genre is listed, you can create a frequency dictionary from all_genres:

```python
count_genres = {} #create your empty frequency dictionary
for genre in all_genres: #iterate through each listed genre
    if genre in count_genres.keys(): #if it's already in the dictionary
        count_genres[genre] = count_genres[genre]+1 #increase the count by 1
    else: #if it's not already in the dictionary
        count_genres[genre] = 1 #add it to the dictionary
```


## Adding Color to your Charts

Adding custom colors to our charts can make them look more beautiful. **To start, create a list of colors:**

```python3
color_list = ['#2CBDFE', '#47DBCD','#F5B14C', '#9D2EC5','#661D98']
```
> This list should be a list of `strings` containing the *hex code* for each color.
>
> Google has a great built in [color picker](https://www.google.com/search?q=color+picker&rlz=1C1GCEA_enUS897US897&oq=color+picker&aqs=chrome.0.69i59j0i512l9.1382j0j7&sourceid=chrome&ie=UTF-8&safe=active&ssui=on).

### [Bar Chart]

To incorporate these colors into a bar chart:
```python3 {linenos=table, hl_lines=["4"]}
plt.bar(
    frequency_series.index,
    frequency_series.values,
    color=color_list
)
```


{{< figure src="images/courses/cs9/unit01/resources_02.png" width="100%" >}}

### [Pie Chart]

```python3 {linenos=table, hl_lines=["5"]}
plt.pie(
    frequency_series.values,            
    labels = frequency_series.index,  
    autopct='%1.1f%%',
    colors=color_list
)     
```


{{< figure src="images/courses/cs9/unit01/resources_03.png" width="100%" >}}

### [Advanced Color]

If you're interested learning how to customize your graphs further, take a look at [`seaborn`](https://seaborn.pydata.org/index.html).

Seaborn is another Python library that is built on top of MatPlotLib.

--- -->
