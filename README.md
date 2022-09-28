Ex-04-Multivariate-Analysis
AIM: 
To apply multivariate analysis on a give data set.

Algorithm:

Step 1.start

Step 2.read the dta from the file

Step 3.clean the data a)remove outliers b)fill the null value or drop the column

Step 4.perform multivariate analysis a)scatter plot b)box plot c)heat map

Program: read and cleaned the null value: code: 
import pandas as pd

df=pd.read_csv("/content/SuperStore.csv")

df['Postal Code']=df['Postal Code'].fillna(df['Postal Code'].mode()[0])

df.isnull().sum()

image

scatter plot:

df.dtypes:

code:

df.dtype

output:

image

kurtosis:

df.kurtosis()

code:

output:

image

scatter plot:

code:

import pandas as pd

import seaborn as sns

sns.boxplot(df['Sales'],df['Postal Code'])

output:

image

Bar plot:

code:

sns.barplot(x=df["Sales"],y=df["Postal Code"],data=df)

image

bar plot

code:

import pandas as pd

import seaborn as sns

import matplotlib.pyplot as plt

states=df.loc[:,["Postal Code","Sales"]]

states=states.groupby(by=["Postal Code"]).sum().sort_values(by="Sales")

plt.figure(figsize=(17,7))

sns.barplot(x=states.index,y="Sales",data=states)

plt.xticks(rotation = 90)

plt.xlabel=("Postal Code")

plt.ylabel=("Sales")

plt.show()

output:

image

code:

import pandas as pd

import seaborn as sns import matplotlib.pyplot as plt

states=df.loc[:,["State","Postal Code"]]

states=states.groupby(by=["State"]).sum().sort_values(by="Postal Code")

plt.figure(figsize=(17,7))

sns.barplot(x=states.index,y="Postal Code",data=states)

plt.xticks(rotation = 90)

plt.xlabel=("Sales")

plt.ylabel=("Postal Code")

plt.show()

output:

image

corr:

df.corr()

output:

image

Heatmap:

code:

import numpy as np

import seaborn as sn

import matplotlib.pyplot as plt

data=pd.read_csv("/content/SuperStore.csv")

data = np.random.randint(low = 1, high = 100, size = (10, 10))

print("The data to be plotted:\n")

print(data)

hm = sn.heatmap(data = data)

plt.show()

output: image

RESULT:

Thus we have applied the multiivariate analysis sucessfully
