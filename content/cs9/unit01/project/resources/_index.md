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

```python
age_df.head()

	name	age
0	Alice	10
1	Bob	    15
2	Charlie	25
3	David	40
4	Sally	80
```
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
df['is_adult']  = df.apply(lambda row: is_adult(row['age']), axis=1)
```
📖 **Here is the updated dataframe.**
```python
age_df.head()

	name	age     is_adult
0	Alice	10      False
1	Bob	    15      False
2	Charlie	25      True
3	David	40      True
4	Sally	80      True
```

*This tutorial is based of [this](https://saturncloud.io/blog/how-to-create-a-new-column-based-on-the-value-of-another-column-in-pandas/#:~:text=Once%20we%20have%20had%20our,and%20return%20a%20new%20DataFrame.) guide.*


---

## Find the mode of a column for each unique value in another column 

📖 **Here is a `dataframe` stored in the variable `age_df`.** It stores names, ages, is_adult, and house.

```python
age_df.head()

	name	age     is_adult    house
0	Alice	10      False       'fire'
1	Bob	    15      False       'metal'
2	Charlie	25      True        'metal'
3	David	40      True        'fire'
4	Sally	80      True        'fire
```

📖 **We want to see what is the `mode` of `is_adult` for each `house`.** For this we must use `groupby`. 

```python
mode_isAdult_by_house_df =  df.groupby(['house'])['is_adult'].agg(pd.Series.mode).to_frame().reset_index()
```

📖 **Here is the new dataframe `mode_isAdult_by_house_df`.**
> For `metal`, because `True` and `False` appear the same amount of times it returns both options. 

```python
mode_isAdult_by_house_df

	house	is_adult         
0	fire	True             
1	metal	['False','True']

```

*This tutorial is based of [this](https://stackoverflow.com/questions/15222754/groupby-pandas-dataframe-and-select-most-common-value) post.*

---


---

## Find the mean of a column for each unique value in another column 

📖 **Here is a `dataframe` stored in the variable `age_df`.** It stores names, ages, is_adult, and house.

```python
age_df.head()

	name	age     is_adult    house
0	Alice	10      False       'fire'
1	Bob	    15      False       'metal'
2	Charlie	25      True        'metal'
3	David	40      True        'fire'
4	Sally	80      True        'fire
```

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

	is_adult	    age         
0	True	    27.500000           
1	False	    47.333333

```






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
