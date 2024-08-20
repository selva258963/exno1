# EX NO : 1

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output

##                                                                                  Data Cleaning Process


```
import pandas as pd
x=pd.read_csv("/content/SAMPLEIDS.csv")
x
```
![image](https://github.com/user-attachments/assets/1305980f-19d7-4717-a2e7-9016cb5d6db4)
```
x.isnull()
```
![image](https://github.com/user-attachments/assets/4a1197d7-5edc-410f-aa0d-feed211a6cf5)
```
x.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/06529a5f-53a9-4887-a741-7ce3c7a0cea2)
```
x.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/88572381-f2d6-4ca8-9a70-f9af2e963a43)
```
y=x[x['TOTAL'] > 300]
y
v = x[x['NAME'].str.startswith('S') | x['NAME'].str.startswith('H')]
v
```
![image](https://github.com/user-attachments/assets/3f652c44-82f3-4932-8dbc-42429185ed76)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/673b62f9-a9b0-4543-b184-35c654a9be83)
```
y.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/6a5bfb7c-a468-4765-a11e-1acaba53e892)

## IQR(Inter Quartile Range)

```
import pandas as pd
import seaborn as sns
g=pd.read_csv("/content/iris.csv")
g
```
![image](https://github.com/user-attachments/assets/81474f79-1c1d-40f8-85b2-c75d356533e0)
```
g.shape
g.describe()
```
![image](https://github.com/user-attachments/assets/9e78fb6d-e538-4ff0-8e7d-473a8d7f8b85)
![image](https://github.com/user-attachments/assets/78a605bc-4a93-4085-9a5c-e4b9d59c3f8b)
```
sns.boxplot(x='sepal_width',data=g)
c1=g.sepal_width.quantile(0.25)
c3=g.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/44fa307f-4631-4c59-bb65-ac65834512b2)
```
rid=g[((g.sepal_width<(c1-1.5*iq))|(g.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
delid=g[~((g.sepal_width<(c1-1.5*iq))|(g.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/b7874134-3d42-490b-910e-58fb32a2a045)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/d3132c26-739e-43fc-86cf-996369c7177e)

## Z-SCORE

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/7f847f9d-12d3-4966-8944-d23097430b3d)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
low = q1 - 1.5*iqr
low
high = q3 + 1.5*iqr
high
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/4b245d57-405c-4ec3-a742-62e2724b4e4f)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/9ebe54ec-4cf4-4e0a-b40a-452c0ef53330)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/33e8181b-cfdb-4001-88bb-59a6182eaa95)

# Result
The given data is successfully performed data cleaning.
