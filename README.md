Ex-04-Multivariate-Analysis

AIM:

To perform Multivariate EDA on the given data set.

EXPLANATION:

Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

ALGORITHM:

STEP 1
Import the built libraries required to perform EDA and outlier removal.


STEP 2
Read the given csv file.


STEP 3
Convert the file into a dataframe and get information of the data.


STEP 4
Return the objects containing counts of unique values using (value_counts()).


STEP 5
Plot the counts in the form of Histogram or Bar Graph.


STEP 6
Use seaborn the bar graph comparison of data can be viewed.


STEP 7
Find the pairwise correlation of all columns in the dataframe.corr() .


STEP 8
Save the final data set into the file.


PROGRAM:
Developed by    : Akash Kumar B
Register number : 212221040011


import pandas as pd
import numpy as np
import seaborn as sbn
import matplotlib.pyplot as plt

d = pd.read_csv("D:\ggg\clg\Documents\SEM 3\Data Science\Projects\Ex-04-Multivariate-Analysis\SuperStore.csv")
d.head()

d.info()
d.describe()
d.isnull().sum()

d['Postal Code'] = d["Postal Code"].fillna(d['Postal Code'].mode()[0])
d.isnull().sum()

sbn.scatterplot(d['Postal Code'],d['Sales'])

states=d.loc[:,["State","Sales"]]
states=states.groupby(by=["State"]).sum().sort_values(by="Sales")
plt.figure(figsize=(17,7))
sbn.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("STATES")
plt.ylabel=("SALES")
plt.show()

states=d.loc[:,["State","Postal Code"]]
states=states.groupby(by=["State"]).sum().sort_values(by="Postal Code")
plt.figure(figsize=(17,7))
sbn.barplot(x=states.index,y="Postal Code",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("STATES")
plt.ylabel=("Postal Code")
plt.show()

states=d.loc[:,["Segment","Sales"]]
states=states.groupby(by=["Segment"]).sum().sort_values(by="Sales")
plt.figure(figsize=(10,7))
sbn.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("SEGMENT")
plt.ylabel=("SALES")
plt.show()

sbn.barplot(d['Postal Code'],d['Ship Mode'],hue=d['Region'])
d.corr()
sbn.heatmap(d.corr(),annot=True)
