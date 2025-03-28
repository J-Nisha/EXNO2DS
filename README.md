# EXNO2DS
```
NAME:Nisha.J
REGISTER NUMBER:212223040133
```
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/titanic_dataset.csv")
df
```
![Screenshot 2025-03-28 101831](https://github.com/user-attachments/assets/35ec6f52-a20e-4571-855a-ff9d7d8e54e9)
```
df.info()
```
![Screenshot 2025-03-28 102417](https://github.com/user-attachments/assets/c3c57028-370b-4c86-b258-d0b86fa197e7)
```
df.set_index("PassengerId",inplace =True)
df.shape
```
![Screenshot 2025-03-28 102457](https://github.com/user-attachments/assets/8cb105ee-e824-4039-8f80-80775b08c93a)
```
df.nunique()
```
![Screenshot 2025-03-28 102535](https://github.com/user-attachments/assets/8f5f9a46-5016-4130-83ef-f480cb1b381d)
```
df["Survived"].value_counts()
```
![Screenshot 2025-03-28 102707](https://github.com/user-attachments/assets/2bc90033-ed4f-4ea1-8422-f5403ab82c93)
```
per=(df['Survived'].value_counts()/df.shape[0]*100).round(2)
per
```
![Screenshot 2025-03-28 102746](https://github.com/user-attachments/assets/c3475a00-0ee4-4b96-bbd1-9849ef1645a4)
```
sns.countplot(data=df,x="Survived")
```
![Screenshot 2025-03-28 102949](https://github.com/user-attachments/assets/6a8a8911-2139-45b2-b651-45e4fbe7a56c)
```
fig, ax1 = plt.subplots(figsize=(5,5))
graph=sns.countplot(ax=ax1,x= 'Survived', data=df)
graph.set_xticklabels (graph.get_xticklabels (), rotation=90)
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2., height + 0.1, height,ha="center")
```
![Screenshot 2025-03-28 103027](https://github.com/user-attachments/assets/19713969-f640-4f71-bc88-71a9fab61628)
```
df.Pclass.unique()
```
![Screenshot 2025-03-28 103231](https://github.com/user-attachments/assets/7204ce33-fdfc-45cd-9565-1f7ed3de2641)
```
df.rename(columns = {'Sex':"Gender"},inplace=True)
df
```
![Screenshot 2025-03-28 103403](https://github.com/user-attachments/assets/1089c101-e51a-4ed8-adce-5748a6ae74ab)
```
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
```
![Screenshot 2025-03-28 103451](https://github.com/user-attachments/assets/d2e6a460-c24d-4985-9744-f886b314bb27)
```
fig, ax1 = plt.subplots(figsize=(8,5))
graph=sns.countplot(ax=ax1,data=df,x="Survived", hue="Pclass", palette="rainbow")
graph.set_xticklabels (graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height+ 20.8, height,ha="left")
```
![Screenshot 2025-03-28 103539](https://github.com/user-attachments/assets/7ea66420-bfaa-4090-9b68-18e753a1d30a)
```
df.boxplot(column="Age",by="Survived")
```
![Screenshot 2025-03-28 104009](https://github.com/user-attachments/assets/b933d647-7a05-4c68-9505-cdcfa1bfabb1)
```
sns.scatterplot(x=df["Age"],y=df["Fare"])
```
![Screenshot 2025-03-28 104057](https://github.com/user-attachments/assets/9813ea16-f9f7-4c71-8995-2028fa472de3)
```
sns.jointplot(x="Age",y="Fare",data=df)
```
![Screenshot 2025-03-28 104204](https://github.com/user-attachments/assets/933f27da-3413-46ef-979c-6e31058d9595)
```
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue="Gender",data=df)
```
![Screenshot 2025-03-28 104309](https://github.com/user-attachments/assets/d773f32a-24a3-4438-b0dc-295f13ec09d1)
```
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![Screenshot 2025-03-28 104508](https://github.com/user-attachments/assets/fb95d752-6596-46c4-aa9d-c8c5e988c8f6)
```
g= sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass", kind = "count", legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax =g.facet_axis(0,0)
for p in ax.patches:
   ax.text(p.get_x()-0.01,p.get_height()*1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')
```
![Screenshot 2025-03-28 104704](https://github.com/user-attachments/assets/86087577-cea0-45f0-9a58-0d71ce946838)
```
corr=df.corr()
sns.heatmap(corr,annot=True)
```
![Screenshot 2025-03-28 104837](https://github.com/user-attachments/assets/9e131d98-6bad-46bb-a72f-29c38932e663)
```
sns.pairplot(df)
```
# RESULT
        <<INCLUDE YOUR RESULT HERE>>
