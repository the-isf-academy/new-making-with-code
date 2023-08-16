---
title: 3. Summary Statistics
# draft: True
---

# Summary Statistics Lab
In this lab, you will practice using Jupyter Notebook and write algorithms to calculate statistics about datasets.

## [0] Pseudocode

How do you make sense of lots of data? You can summarize it with statistics!

#### Calculate The Central Tendency
When you have a ton of data, you might want to find one number to summarize the data. How about the middle?  

Here are three ways to find the middle: 
- Mean: the average of a list of numbers
- Median: the middle number in a sorted list of numbers
- Mode: value that appears most frequently in a data set


In this lab, we will write the algorithms to find the median, mean, and mode of a list of numbers. Before jumping into the Python code, let’s write the pseudocode so we can be sure our algorithm works as intended.


{{< write-action "In groups, work through the Summary Stats Lab Worksheet." >}} 

{{< checkpoint >}}
Check in with a teacher before moving onto the translating your pseudocode into Python code.
{{< /checkpoint >}}

## [1] Translating Pseudocode

### [Setup]

Now that you are confident in your algorithms, try to translate them into Python code.

{{< code-action >}} **Starter code for the lab is provided in the `lab-sumstats` repo.** 
```shell
cd cs9/unit_01
git clone https://github.com/the-isf-academy/lab-sumstats-YOUR-GITHUB-USERNAME.git
```

### [sumstats.ipynb]

{{< code-action >}} **Open the `sumstats.ipynb` file by typing `jupyter notebook` in your Terminal.** Be sure to read cell by cell, and follow along with instructions.

*Each person should write their own code, but you can work together to complete each function.*

### [Deliverables]


{{< deliverables >}}
For this lab, you should submit the following...

- Your `sumstats.ipynb` file with code for each of the following functions:
    - `calculate_mean()`
    - `calculate_median()`
    - `calculate_mode()`

Also be sure to hand in your Summary Stats Lab Worksheet.
{{< /deliverables >}}

---

## [2] Solutions

Below are correctly ordered pseudocode and code solutions for each of the required functions. 

{{< code-action >}} **Use the solutions to fill in your `sumstats.ipynb` file.**

### [Mean]

{{< expand "Pseudocode" >}}
```
Count how many numbers are in the list -> store in count
Add up the numbers in the list -> store in sum
Divide ‘sum’ by ‘count’ -> store in mean
Return mean
```
{{< /expand >}}

{{< expand "Translated Python Code " >}}
```python
def calculate_mean(alist):
    total_sum = sum(alist)
    mean_val = total_sum / len(alist)
    return mean_val
```
{{< /expand >}}

### [Median]

{{< expand "Pseudocode" >}}
#### Pseudocode 

```
Sort numbers in the list from smallest to largest -> store in sorted_list
Count how many numbers are in the list -> store in count

If count is even
    Divide the count by two and subtract one -> store in index 
    Add the values of sorted_list at index  and index +1 -> store in middle_sum
    Divide middle_sum by 2 -> store in median_number

If, count is odd 
    Divide the count by two and round down to the nearest integer -> store in index
    Index sorted_list at index -> store value in median_number

Return median_number
```
{{< /expand >}}


{{< expand "Translated Python Code" >}}

```python
def calculate_median(alist):
    sorted_list = sorted(alist)
    count = len(alist)

    if count%2 == 0:
        index = (count//2) - 1
        middle_sum = sorted_list[index] + sorted_list[index+1]
        median_number = middle_sum/2
    else:
        index = count//2
        median_number = sorted_list[index]

    return median_number
```
{{< /expand >}}

### [Mode]
#### `create_counts_dict()`

{{< expand "Pseudocode" >}}
```
Create empty dictionary -> store in mode_dictionary 

Loop through the list of items

If current item is not a key in mode_dictionary
	Add current item as a key to mode_dictionary with the value of 1

If current item is a key in mode_dictionary
	Add 1 to the value of the current item key in mode_dictionary

Return mode_dictionary
```
{{< /expand >}}

{{< expand "Translated Python Code" >}}


```python
def create_counts_dict(alist):
    mode_dictionary = {}

    for item in alist:
        if item in mode_dictionary:
            mode_dictionary[item] = mode_dictionary[item] + 1
        else:
            mode_dictionary[item] = 1

    return mode_dictionary
```
{{< /expand >}}


#### `caculate_mode()`

{{< expand "Pseudocode" >}}
```
Create frequency dictionary from list -> store in mode_dictionary
Create a variable that holds `None` -> store in ‘mode_key’

Iterate through the key, value pairs of the frequency dictionary 
	If ‘mode_key’ is `None`
		Set ‘mode_key’ to the current `key`
	If the value of the frequency dictionary at `mode_key` is less than the current value
		Set `mode_key` to key 

Return `mode_key`
```
{{< /expand >}}

{{< expand "Translated Python Code" >}}

```python
def calculate_mode(alist):
    mode_dictionary = create_counts_dict(alist)
    mode_key = None

    for key,value in mode_dictionary.items():
        if mode_key == None:
            mode_key = key
        if mode_dictionary[mode_key] < value:
            mode_key = key

    return mode_key
```
{{< /expand >}}
