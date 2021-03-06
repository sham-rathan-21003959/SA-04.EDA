# <p align ='center'> Perform EDA with given Dataset </p>
## Name     : S.SHAM RATHAN
## Reg.no   : 212221230093
## Dept     : AIDS
## Sa Assignment : 04.
-----------------------------------------------------------------------
### Packages:
```
import pandas as pd
import numpy as np
import seaborn as sns
```
### Initial DataFrame:
```
df=pd.read_csv("food-price-index-2021.csv")
df
```
![output](./pic/1.png)
### Number of Rows and Columns in the DataFrame:
```
df.info()
```
![output](./pic/2.png)
### Sum of null data value present in each column:
```
df.isnull().sum()
```
![output](./pic/3.png)
### Graphical Representation - Before removing Outliers:
```
df["Data_value"]=df["Data_value"].fillna(df["Data_value"].median())
df.isnull().sum()
df.boxplot()
```
![output](./pic/4.png)
### Statistical Method (IQR) to remove Outliers from Dataset:
```
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
print(IQR)
df_out = df[~((df < (Q1 - 1.5 * IQR)) |(df > (Q3 + 1.5 * IQR))).any(axis=1)]
print(df_out.shape)
```
![output](./pic/5.png)
### Graphical Representation - After removing Outliers:
```
df_out.boxplot()
```
![output](./pic/6.png)
### Infromation on Number of rows and columns after removing Ouliers:
```
df_out.info()
```
![output](./pic/7.png)
## EDA
### Insight about data in Column -Series_reference:
```
df["Series_reference"].value_counts()
df_out["Series_reference"].value_counts()
```
![output](./pic/8.png)
### Insight about data in Column -Period :
```
df["Period"].value_counts()
df_out["Period"].value_counts()
```
![output](./pic/9.png)
### Insight about data in Column -Data_value :
```
df["Data_value"].value_counts()
df_out["Data_value"].value_counts()
```
![output](./pic/10.png)
### Insight about data in Column -Series_title_1:
```
df["Series_title_1"].value_counts()
df_out["Series_title_1"].value_counts()
```
![output](./pic/11.png)
### DataSet after removing Outlier
```
df_out
```
![output](./pic/12.png)
### Correlation of columns:
```
df_out.corr()
sns.heatmap(df_out.corr(),annot=True)
df.corr()
sns.heatmap(df.corr(),annot=True)
```
![output](./pic/13.png)
<br></br>
<br></br>
<br></br>

![output](./pic/14.png)
### Analyzation of Column - Data_value:
```
sns.countplot(x="Data_value",data=df_out)
```
![output](./pic/15.png)
### Analyzation of Column - Period:
```
sns.countplot(x="Period",data=df_out)
```
![output](./pic/16.png)
### Non Categorical Data- Distributive Plot:
```
sns.displot(df_out["Period"])
sns.displot(df_out["Data_value"])
```
![output](./pic/17.png)
![output](./pic/18.png)
### Statistical Method - Cross tabulation:
```
pd.crosstab(df_out["Data_value"],df_out["Series_title_1"])
pd.crosstab(df_out["Period"],df_out["Series_title_1"])
```
![output](./pic/19.png)
![output](./pic/20.png)

# <p align ='center'> Thank You </p>






