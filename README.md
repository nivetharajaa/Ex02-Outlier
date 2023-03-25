# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

##Aim:
###TO detect and remove the outliers in the given data set and save the final data.

##Algorithm:

##Step 1
###Import the required packages(pandas,numpy,scipy)

##Step 2
###Read the given csv file

##Step 3
###Convert the file into a dataframe and get information of the data.

##Step 4
###Remove the non numerical data columns using drop() method.

##Step 5
###Detect the outliers in the data set using z scores method.

##Step 6
###Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

##Step 7
###Check if the outliersare removed from data set using graphical methods.

##Step 8
###Save the final data set into the file.

##Program:

###1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

###Program developed by : A.Nivetha

###Register number : 212222230101

import pandas as pd

import numpy as np

import seaborn as sns

df = pd.read_csv("/content/bhp.csv")

df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25)

q3 = df['price_per_sqft'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]

df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)

##(3)Examine price_per_sqft column and use zscore of 3 to remove outliers.
from scipy import stats

z = np.abs(stats.zscore(df['price_per_sqft']))

df2 = df[(z<3)]

df2

print(df2.shape)

sns.boxplot(x="price_per_sqft",data=df2)

##(4)(i) For the data set height_weight.csv detect weight outliers using IQR method.
import pandas as pd

import numpy as np

import seaborn as sns

df = pd.read_csv("/content/height_weight - Sheet1.csv")

df

df.head()

df.info()

df.describe()

df.isnull().sum()

df.shape

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df1 =df[((df['weight']>=ll)&(df['weight']<=ul))]

df1

df1.shape

sns.boxplot(x="weight",data=df1)

##(4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
sns.boxplot(x="height",data=df)

q1 = df['height'].quantile(0.25)

q3 = df['height'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df2 =df[((df['height']>=ll)&(df['height']<=ul))]

df2

df2.shape

sns.boxplot(x="height",data=df2)

##Output:

##(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

##Dataset:

![Screenshot from 2023-03-25 11-11-01](https://user-images.githubusercontent.com/120543388/227699686-3924a125-2079-4b6d-846e-736c52ddac94.png)

##Dataset Head :

![Screenshot from 2023-03-25 11-32-06](https://user-images.githubusercontent.com/120543388/227699972-58a3fda0-541e-470b-bb0b-e55f2baf7d58.png)

Dataset Info :

![Screenshot from 2023-03-25 11-38-51](https://user-images.githubusercontent.com/120543388/227700029-4f2da569-27a9-47d9-95f5-a60f4c158be8.png)

Dataset Describe:

![Screenshot from 2023-03-25 11-40-21](https://user-images.githubusercontent.com/120543388/227700121-881f78cf-e0bf-4b82-945a-d63289eaa6d4.png)
