# Programming Assignment 4 Data Wrangling and Data Visualization

### Objectives

1. To identify the codes and functions needed for cleaning and visualizing data
2. To be able to apply and use the different codes and functions in creating a Python program that will be used in data wrangling and data visualization

### Programming Assignment 4

PA4: https://github.com/itzWyntr/ECE2112_PA4_BAAS_2ECEB/blob/main/PA4.ipynb

## Table of Contents

Objectives: https://github.com/itzWyntr/ECE2112_PA4_BAAS_2ECEB/edit/main/README.md#objectives

Programming Assignment: https://github.com/itzWyntr/ECE2112_PA4_BAAS_2ECEB/blob/main/PA4.ipynb

Problem 1: https://github.com/itzWyntr/ECE2112_PA4_BAAS_2ECEB/edit/main/README.md#problem-1-dataframe-creation

Problem 2: https://github.com/itzWyntr/ECE2112_PA4_BAAS_2ECEB/edit/main/README.md#problem-2-graph-creation

## Programming Assignment

Initially 

Import Pandas
``` python
import pandas as pd
```

Download and call the Excel file
``` python
df = pd.read_excel('board2.xlsx')
```

### Problem 1: Dataframe Creation
This programming assignment is divided into 2 parts

a. Create a dataframe showing students who took instrumentation, Luzon as their hometown, and a grade greater than 70 in Electronics. Display their Name, grade in GEAS and Electronics

Use indexing to get the given conditions. Display their Name and grade in both GEAS and Electronics
``` python
Instru = df.loc[(df['Track']=='Instrumentation')&(df['Hometown']=='Luzon')&(df['Electronics']>70),['Name', 'GEAS', 'Electronics']]
Instru
```

b. Create a dataframe showing students whose hometown is in Mindanao, female, and average grade is greater than or equal to 55. Display the name, track, grade in electronics, and the average grade

1. Create a column 'Ave' that contains the average grade from Math, Electronics, GEAS, and Communication
```python
df['Ave']=df[['Math', ' Electronics', 'GEAS', 'Communication']].mean(axis=1)
```
.mean is used to get the average and (axis=1) to get the mean row-wise

2. Use indexing to call the given conditions and display the name, track, grade in electronics, and the average grade
```python
df['Ave']=df[['Math','Electronics','GEAS','Communication']].mean(axis=1) #Mean takes average, axis takes the average of the row
Mindy = df.loc[(df['Hometown']=='Mindanao')&(df['Gender']=='Female')&(df['Ave']>=55),['Name', 'Track', 'Electronics','Ave']]
Mindy
```

### Problem 2: Graph Creation

Create Visualization that shows different features that contributes to average grade

Initially, import matplotlib

```python
import matplotlib.pyplot as plt
```

a. Average by Track

1. To get distinct Tracks
```python
tracks = df['Track'].unique()
```
2. Create a bar graph
```python
plt.bar(tracks, [df[df['Track'] == t]['Ave'].mean() for t in tracks])
```
"for t in tracks" looks at each category one by one, while "==t" filters the rows that belong to that category.


b. Average by Gender 

Same as the first and second steps on at a.
```python
genders = df["Gender"].unique()
plt.bar(genders, [df[df["Gender"] == g]["Ave"].mean() for g in genders])
```

c. Average by Hometown
Also same steps as the first
```python
hometowns = df["Hometown"].unique()
plt.bar(hometowns, [df[df["Hometown"] == h]["Ave"].mean() for h in hometowns])
```





