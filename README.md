# Ex-08-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.

# CODE
## Data pre-processing
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/Superstore.csv",encoding="ISO-8859-1")
df
df.isnull.sum()
df.info()
df.describe()
```
## Which Segment has Highest sales?
```
sns.lineplot(x="Segment",y="Sales",data=df,marker='o')
plt.title("Segment vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Segment",y="Sales",data=df)
plt.xticks(rotation = 90)
plt.show()
```

## Which City has Highest profit?
```
df.shape
df1 = df[(df.Profit >= 60)]
df1.shape

plt.figure(figsize=(30,8))
states=df1.loc[:,["City","Profit"]]
states=states.groupby(by=["City"]).sum().sort_values(by="Profit")
sns.barplot(x=states.index,y="Profit",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()
```
## Which ship mode is profitable?
```
sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()

sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.show()
```
## Sales of the product based on region.
```
states=df.loc[:,["Region","Sales"]]
states=states.groupby(by=["Region"]).sum().sort_values(by="Sales")
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("Region")
plt.ylabel=("Sales")
plt.show()

df.groupby(['Region']).sum().plot(kind='pie', y='Sales',figsize=(6,9),pctdistance=1.7,labeldistance=1.2)
```
## Find the relation between sales and profit.
```
df["Sales"].corr(df["Profit"])

df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()

sns.pairplot(df_corr, kind="scatter")
plt.show()
```
## Segment
```
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```
## City
```
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```
## States
```
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```
## Segment and Ship Mode
```
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()
```
## Segment, Ship mode and Region
```
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.xlabel('Segment - Ship Mode')
plt.ylabel('Value')
plt.legend(title='Region')
plt.show()
```


# OUPUT
## Data pre-processing
![11](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/0c111f3a-88d0-4ccf-b848-ad186002212d)
![12](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/e3633c27-2b60-4762-9a1c-99f9fad68ca1)
![13](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/3d09f7c0-b146-46f7-9503-d64fbbabc63c)
![14](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/86ce96bd-6b1e-48fb-bdb1-746556a7cac1)

## Which Segment has Highest sales?
![15](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/88134d7b-6ade-4e68-9a6c-8dbb1e3e8219)

## Which City has Highest profit?
![16](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/37fcff25-c4c9-48cc-8e29-5a4ca9f4a182)

## Which ship mode is profitable?
![17](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/259c2b66-9f1e-4282-a1c9-1c09dedce37a)

## Sales of the product based on region.
![19](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/358c6578-c879-45bb-95fe-d428a58b52da)
![20](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/358cbbac-6aad-44ec-b70c-db2494094b0c)

## Find the relation between sales and profit.
![21](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/813811fb-5f27-40ba-af82-de928cb9ce03)
![22](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/8b871732-9487-4ece-983b-bbb723c35be3)



## Segment
![23](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/1f9246ae-3486-4696-bc55-7e4b8a4f02d6)

## City
![24](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/639978e7-2e1f-45e6-9346-300cdc73cd41)

## States
![25](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/c9da43ba-85e4-4607-9ca6-d113b6059aa5)

## Segment and Ship Mode
![26](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/1554450f-27e0-4890-af23-de465fdf7a39)

## Segment, Ship mode and Region
![27](https://github.com/premalatha-sureshbabu/Ex-08-Data-Visualization-/assets/120620842/28de5ff2-1d26-4550-9716-6de6773f0cf7)

# Result:
Thus, Data Visualization is performed on the given dataset and save the data to a file.
