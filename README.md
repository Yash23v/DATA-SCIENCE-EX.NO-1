#EX.NO:1
Data Cleaning Process

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
```
import pandas as pd
data=pd.read_csv("sampleids.csv")
data
```
<img width="881" height="687" alt="Screenshot 2026-05-26 082546" src="https://github.com/user-attachments/assets/a16aef48-4011-4dde-9068-c4fae158b178" />

```
data.info()
```
<img width="383" height="406" alt="Screenshot 2026-05-26 082614" src="https://github.com/user-attachments/assets/5e8c65fe-6765-46e0-af19-3a89d15a86d2" />

```
print(data.head())
print(data.tail())
```
<img width="772" height="562" alt="Screenshot 2026-05-26 082737" src="https://github.com/user-attachments/assets/c3e8fb99-b1f8-4d36-b297-a5b0c248eb14" />

```
data.isnull()
```
<img width="748" height="680" alt="Screenshot 2026-05-26 082842" src="https://github.com/user-attachments/assets/76bfb6f0-cc35-4e0e-b6d2-f7e1ae524df3" />

```
data.isnull().sum()
```
<img width="133" height="284" alt="Screenshot 2026-05-26 082906" src="https://github.com/user-attachments/assets/aaf64378-897e-4a22-b958-9927070a2ce3" />

```
data.dropna()
```
<img width="876" height="439" alt="Screenshot 2026-05-26 082921" src="https://github.com/user-attachments/assets/141e927b-ad9c-41ce-b4cf-1bf570f7ca01" />

```
data.fillna(method='ffill')
```
<img width="881" height="684" alt="ffil" src="https://github.com/user-attachments/assets/d01d204c-d23f-476e-a707-40807490623f" />

```
data.fillna(method='bfill')
````
<img width="868" height="683" alt="bfil" src="https://github.com/user-attachments/assets/bab3b313-61d0-4b4b-a6b4-2810f7cc3faa" />

```
data.fillna({'NAME':'RIYA','GENDER':'FEMALE','ADDRESS':'CHENNAI','M1':90,'M2':90,'M3':89,'M4':87})
```
<img width="869" height="683" alt="Screenshot 2026-05-26 083203" src="https://github.com/user-attachments/assets/86eb4689-f170-4534-aa0b-7df1057abb55" />


```
import numpy as np
from scipy import stats
ir=pd.read_csv("iris.csv")
ir
```
<img width="521" height="418" alt="Screenshot 2026-05-26 083230" src="https://github.com/user-attachments/assets/aca360bd-9d3a-469c-b97f-bfd922e86ecb" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="673" height="572" alt="Screenshot 2026-05-26 083258" src="https://github.com/user-attachments/assets/9836f60a-bdb7-4fca-b99a-0b6d7b4df778" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
print()
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
print(rid['sepal_width'])
```
<img width="332" height="155" alt="Screenshot 2026-05-26 083854" src="https://github.com/user-attachments/assets/4483b6a7-2bbf-4e59-af78-42f7f8ed7abc" />

```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```
<img width="531" height="420" alt="Screenshot 2026-05-26 083911" src="https://github.com/user-attachments/assets/e468edc6-43b4-4e2c-9f55-db20211ba7be" />

```
sns.boxplot(x='sepal_width',data=delid)
```
<img width="674" height="584" alt="Screenshot 2026-05-26 084431" src="https://github.com/user-attachments/assets/a0b7bba9-e19b-4569-9aa7-af5cbfb19e76" />

```
z=np.abs(stats.zscore(ir['sepal_width']))
z
```
<img width="457" height="260" alt="Screenshot 2026-05-26 084449" src="https://github.com/user-attachments/assets/9cdb5403-2299-441d-af90-8a105d0931c2" />

```
ir1=ir[z<3]
ir1
```
<img width="533" height="424" alt="Screenshot 2026-05-26 084644" src="https://github.com/user-attachments/assets/aaba2be1-8928-4444-a7c2-940991a38460" />

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
