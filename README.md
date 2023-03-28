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

##Dataset Info :

![Screenshot from 2023-03-25 11-38-51](https://user-images.githubusercontent.com/120543388/227700029-4f2da569-27a9-47d9-95f5-a60f4c158be8.png)

##Dataset Describe:

![Screenshot from 2023-03-25 11-40-21](https://user-images.githubusercontent.com/120543388/227700121-881f78cf-e0bf-4b82-945a-d63289eaa6d4.png)

##Null Values:

![Screenshot from 2023-03-27 21-18-37](https://user-images.githubusercontent.com/120543388/227994366-3f65fb30-38e2-4a86-b21e-04138acdcccc.png)

##Dataset Shape:

![Screenshot from 2023-03-27 21-20-40](https://user-images.githubusercontent.com/120543388/227994839-22beb4da-c6ef-498d-b8df-12b5fd4799a0.png)

##Box plot of price_per_sqft column with outliers:

![Screenshot from 2023-03-27 21-22-02](https://user-images.githubusercontent.com/120543388/227995246-d0d6bea9-63cc-4d42-82fa-9d46ae4cd0d6.png)

##price_per_sqft - Dataset after removing outliers:

![Screenshot from 2023-03-27 21-23-52](https://user-images.githubusercontent.com/120543388/227995802-a21f1df7-85bb-493b-8fa3-ec59617331cc.png)

##price_per_sqft - Shape of Dataset after removing outliers :

![Screenshot from 2023-03-27 21-25-51](https://user-images.githubusercontent.com/120543388/227996262-e4804b79-1efa-4ddc-b26b-1b961f12d522.png)

##Box Plot of price_per_sqft column without outliers:

![Screenshot from 2023-03-27 21-27-28](https://user-images.githubusercontent.com/120543388/227996686-f464022a-9de8-4609-bb81-cc30dd8f1690.png)

##(3) Examine price_per_sqft column and use zscore of 3 to remove outliers.

###Dataset after removal of outlier using z score:

![Screenshot from 2023-03-27 21-29-16](https://user-images.githubusercontent.com/120543388/228001284-89382c33-5b1a-4b62-a855-f38f4b426f95.png)

##Shape of Dataset after removal of outlier using z score:

![Screenshot from 2023-03-27 21-31-59](https://user-images.githubusercontent.com/120543388/228001703-391b9452-cc7c-4ec7-b44d-fe77bb549bfc.png)

##(4) For the data set height_weight.csv detect weight and height outliers using IQR method:

##Dataset:

![Screenshot from 2023-03-27 21-33-29](https://user-images.githubusercontent.com/120543388/228002208-caf35363-ecb3-4c4d-9cb6-695372f8db20.png)

##Dataset Head:

![Screenshot from 2023-03-27 21-36-36](https://user-images.githubusercontent.com/120543388/228002533-5ed38c2a-d459-4c25-a22e-110627511325.png)

##Dataset Info:

![Screenshot from 2023-03-27 21-51-52](https://user-images.githubusercontent.com/120543388/228002885-dd71a69c-d9ea-4378-b9d8-eb1efd9c3e54.png)

##Dataset Describe:

![Screenshot from 2023-03-27 21-53-33](https://user-images.githubusercontent.com/120543388/228003293-f944fb67-27ba-432c-a70d-734b4f8b5aca.png)

##Null Values:

![Screenshot from 2023-03-27 21-55-23](https://user-images.githubusercontent.com/120543388/228003712-d5627253-58f5-4485-8de2-bee5e920a97e.png)

##Dataset Shape:

![Screenshot from 2023-03-27 21-56-52](https://user-images.githubusercontent.com/120543388/228004083-e659dd57-8cf1-4ec2-8a48-53d7e2bd1819.png)

##Weight - With outliers:

![Screenshot from 2023-03-27 21-58-36](https://user-images.githubusercontent.com/120543388/228004500-1127cf0b-5047-468a-9ce1-c093e24e8155.png)

##Weight - Dataset after removing Outliers using IQR method:

![Screenshot from 2023-03-27 22-00-11](https://user-images.githubusercontent.com/120543388/228004867-21fa6ed9-84b8-441a-809e-e09c6e177fa6.png)

##Weight - Shape of Dataset after removing Outliers using IQR method:

![Screenshot from 2023-03-27 22-02-00](https://user-images.githubusercontent.com/120543388/228005296-108e03bf-5395-4a83-9948-23f68ee6a447.png)

##Weight - Without Outliers using IQR method:

![Screenshot from 2023-03-27 22-04-47](https://user-images.githubusercontent.com/120543388/228006203-257665ae-ddc6-422e-82c1-43b265f16b2c.png)

##Height - With outliers:

![Screenshot from 2023-03-27 22-08-17](https://user-images.githubusercontent.com/120543388/228007215-8aed10f9-7e01-4bc6-8a00-6f794c24d4f3.png)

##Height - Dataset after removing Outliers using IQR method:

![Screenshot from 2023-03-27 22-09-55](https://user-images.githubusercontent.com/120543388/228007558-f05b0825-3888-483b-8fb9-fd691a0c9a70.png)

##Height - Shape of Dataset after removing Outliers using IQR method:

![Screenshot from 2023-03-27 22-11-11](https://user-images.githubusercontent.com/120543388/228007875-c5402a93-c84b-4777-88bd-0727a4a7ac67.png)

##Height - Without Outliers using IQR method:

![Screenshot from 2023-03-27 22-12-11](https://user-images.githubusercontent.com/120543388/228008171-e0186b9f-d397-480f-b6e4-e061e3b86d46.png)

##Result:

###Thus the outliers are detected and removed in the given file and the final data set is saved into the file.












