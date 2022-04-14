### Ex-04-EDA
# AIM:

To perform EDA on the given data set.

# Explanation:

The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

# ALGORITHM:

STEP 1:

Import the required packages(pandas,numpy,seaborn).

STEP 2:

Read and Load the Dataset.

STEP 3:

Remove the null values from the data and remove the outliers.

STEP 4:

Remove the non numerical data columns using drop() method.

STEP 5:

returns object containing counts of unique values using (value_counts()).

STEP 6:

Plot the counts in the form of Histogram or Bar Graph.

STEP 7:

find the pairwise correlation of all columns in the dataframe(.corr()).

STEP 8:

Save the final data set into the file.

# CODE:

```
Developed by:D.vishnu vardhan reddy
Register no:212221230023

import pandas as pd
import numpy as np
import seaborn as sns
df=pd.read_csv("supermarket.csv")
df

#cleaning dataset
#checking for null values
df.isnull().sum()

#data is cleaned, proceed to remove outliers
#checking for outliers
df.boxplot()

#removing outliers
cols = ['Unit price','Quantity','Tax 5%','Total','cogs','gross margin percentage','gross income','Rating']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
df
df.boxplot()

# outliers removed
# performing data analysis
# performing data analysis
# statistical analysis for single data group
df['Branch'].value_counts()
df['City'].value_counts()
df['Customer type'].value_counts()
df['Gender'].value_counts()
df['Product line'].value_counts()
df['Quantity'].value_counts()
df['Payment'].value_counts()

# statistical analysis for two data groups
pd.crosstab(df["Customer type"],df["Branch"])
pd.crosstab(df["Customer type"],df["City"])
pd.crosstab(df["Customer type"],df["Gender"])
pd.crosstab(df["Customer type"],df["Payment"])
pd.crosstab(df["Product line"],df["Quantity"])

# statistical analysis for multiple data groups
#analysing pairwise correlation of columns in dataset
df.corr()

# graphical analysis of categorical data--univariate
sns.countplot(x="Branch",data=df)
sns.countplot(x="City",data=df)
sns.countplot(x="Customer type",data=df)
sns.countplot(x="Payment",data=df)
sns.countplot(x="Gender",data=df)
sns.countplot(y="Product line",data=df)
sns.countplot(x="Quantity",data=df)

# graphical analysis of non-categorical data or data with multiple categories--univariate
sns.displot(df["Unit price"])
sns.displot(df["Tax 5%"])
sns.displot(df["cogs"])
sns.displot(df["gross income"])

# graphical analysis of categorical data--bivariate
sns.countplot(x="City",hue="Customer type",data=df)
sns.countplot(x="Branch",hue="Customer type",data=df)
sns.countplot(x="Gender",hue="Customer type",data=df)
sns.countplot(x="Payment",hue="Customer type",data=df)
sns.countplot(y="Product line",hue="Quantity",data=df)

# graphical analysis of non-categorical data or data with multiple categories--bivariate
sns.displot(df[df["City"]=='Yangon']["cogs"])
sns.displot(df[df["City"]=='Mandalay']["cogs"])
sns.displot(df[df["City"]=='Naypyitaw']["cogs"])

sns.displot(df[df["Product line"]=='Health and beauty']["Gender"])
sns.displot(df[df["Product line"]=='Electronic accessories']["Gender"])
sns.displot(df[df["Product line"]=='Home and lifestyle']["Gender"])
sns.displot(df[df["Product line"]=='Sports and travel']["Gender"])
sns.displot(df[df["Product line"]=='Food and beverages']["Gender"])
sns.displot(df[df["Product line"]=='Fashion accessories']["Gender"])

sns.displot(df[df["Gender"]=='Male']["gross income"])
sns.displot(df[df["Gender"]=='Female']["gross income"])

# Graphical representation of data--multivariate 
df.drop('gross margin percentage',axis=1,inplace=True)
sns.heatmap(df.corr(),annot=True)

```
# OUTPUT:

![OUTPUT](/vishnu/c1.png)
![OUTPUT](/vishnu/c2.png)
![OUTPUT](/vishnu/c3.png)
![OUTPUT](/vishnu/c4.png)
![OUTPUT](/vishnu/c5.png)
![OUTPUT](/vishnu/c6.png)
![OUTPUT](/vishnu/c7.png)
![OUTPUT](/vishnu/c8.png)
![OUTPUT](/vishnu/c10.png)
![OUTPUT](/vishnu/c11.png)
![OUTPUT](/vishnu/c12.png)
![OUTPUT](/vishnu/c13.png)
![OUTPUT](/vishnu/c14.png)
![OUTPUT](/vishnu/c15.png)
![OUTPUT](/vishnu/c16.png)
![OUTPUT](/vishnu/c17.png)
![OUTPUT](/vishnu/c18.png)
![OUTPUT](/vishnu/c19.png)
![OUTPUT](/vishnu/c20.png)
![OUTPUT](/vishnu/c21.png)
![OUTPUT](/vishnu/c22.png)
![OUTPUT](/vishnu/c23.png)

# RESULT :

The data has been cleaned, outlier has been removed and the EDA on the given data has been performed.


