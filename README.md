# Exno:1
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
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
<img width="813" height="701" alt="image" src="https://github.com/user-attachments/assets/16482b4d-f861-4ea6-aa11-6cb2d0b9f13d"/>

```
df.shape
```

<img width="196" height="41" alt="image" src="https://github.com/user-attachments/assets/8ae82d6e-548f-46de-9163-3d2b0dd1c279"/>

```
df.describe()
```

<img width="813" height="701" alt="image" src="https://github.com/user-attachments/assets/d1906e7c-9ee6-464b-9c5d-fc7d707fb1eb" />

```
df.info()
```

<img width="383" height="354" alt="image" src="https://github.com/user-attachments/assets/76e515fc-12e8-42c1-8882-fa33dc037997" />

```
df.head(3)
```

<img width="840" height="125" alt="image" src="https://github.com/user-attachments/assets/f752aa3d-cd43-4cb5-96ac-83515837ff50" />

```
df.tail(3)
```

<img width="839" height="113" alt="image" src="https://github.com/user-attachments/assets/dd7060b5-5372-4253-8f11-46ae5e9a0bd5" />

```
df.isna().sum()
```

<img width="215" height="455" alt="image" src="https://github.com/user-attachments/assets/19a15bd1-2965-4f11-aeff-e3ceff8569e0" />

```
x=df.dropna(how='any')
df
```

<img width="819" height="696" alt="image" src="https://github.com/user-attachments/assets/c9edc38f-8344-46ea-b42e-864614a07029" />

```
x2=df.dropna(how='all').shape
df
```

<img width="819" height="713" alt="image" src="https://github.com/user-attachments/assets/3eba83b0-26a8-4441-83f3-890b7399995f" />

```
mn=df.TOTAL.mean()
mn
```

<img width="70" height="37" alt="image" src="https://github.com/user-attachments/assets/5db016a2-320a-4ffc-b734-59029420a3e9" />

```
df.TOTAL.fillna(mn,inplace=True)
df
```

<img width="835" height="718" alt="image" src="https://github.com/user-attachments/assets/af7bfa16-94c0-4511-8034-1a781bc171e8" />

```
df.isnull().sum()
```

<img width="204" height="455" alt="image" src="https://github.com/user-attachments/assets/e557314f-a6cc-40d4-9d48-7c78e8b81d0b" />

```
df.M1.dropna(inplace=True)
df
```

<img width="827" height="697" alt="image" src="https://github.com/user-attachments/assets/6e3b3604-940a-4f77-bcba-8b8116caef50" />

```
df.M1.fillna(method='ffill',inplace=True)
df
```

<img width="1259" height="755" alt="image" src="https://github.com/user-attachments/assets/7e1e055d-c2b1-4df7-ba64-5facb9f4596d" />

```
df.isnull().sum()
```

<img width="202" height="437" alt="image" src="https://github.com/user-attachments/assets/2dc8b644-6072-4d58-bb99-ca026e8a2153" />

```
df.M2.fillna(method='ffill',inplace=True)
df
```

<img width="1322" height="737" alt="image" src="https://github.com/user-attachments/assets/fc251344-e350-4bb4-b4e4-b88572010269" />

```
df.isnull().sum()
```

<img width="191" height="465" alt="image" src="https://github.com/user-attachments/assets/6b90925e-9d76-4fb3-82aa-447ede25e25a" />

```
df.M3.fillna(method='ffill',inplace=True)
df
```

<img width="1335" height="727" alt="image" src="https://github.com/user-attachments/assets/30dc9f9a-7990-4765-9ece-e65aab2f11c1" />

```
df.isnull().sum()
```

<img width="211" height="450" alt="image" src="https://github.com/user-attachments/assets/69e212cf-7b61-46f9-be95-1faaaada4d33" />

```
df.duplicated()
```

<img width="151" height="746" alt="image" src="https://github.com/user-attachments/assets/8d06218a-4d1b-496e-af33-ec594d7fb282" />

```
df.drop_duplicates(inplace=True)
df
```

<img width="831" height="672" alt="image" src="https://github.com/user-attachments/assets/77697620-e333-4c32-9307-03313bbeb107" />

```
df['DOB']
```

<img width="232" height="681" alt="image" src="https://github.com/user-attachments/assets/00550a53-8756-4997-a937-5a901acaca28" />

```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```

<img width="678" height="501" alt="image" src="https://github.com/user-attachments/assets/90edf468-a82a-4a81-98f4-664ff24e8066" />

```
df.dropna(inplace=True)
df
```

<img width="847" height="570" alt="image" src="https://github.com/user-attachments/assets/54e9e34a-0c2b-4f9b-8c03-cd3513b02122" />

```
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```

<img width="579" height="533" alt="image" src="https://github.com/user-attachments/assets/f163e058-6737-487a-b92d-aaa40ab11d97" />

## OUTLIER DETECTION AND REMOVAL USING IQR
```
import pandas as pd
import seaborn as sns
import numpy as np

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```

<img width="116" height="467" alt="image" src="https://github.com/user-attachments/assets/462a4b8c-a4ef-4c4c-819b-b33fe6067304" />

```
sns.boxplot(data=af)
```

<img width="614" height="454" alt="image" src="https://github.com/user-attachments/assets/b68f2d88-3c1b-48d5-a01f-4a467939ca4c" />

```
sns.scatterplot(data=af)
```

<img width="566" height="442" alt="image" src="https://github.com/user-attachments/assets/0185997c-d87a-4e5f-ad2f-8f3cfec4f3cb" />

```
q1=af.quantile(0.25)
q2=af.quantile(0.50)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```

<img width="154" height="124" alt="image" src="https://github.com/user-attachments/assets/1449e739-cb3b-4f62-a748-5b285f736d07" />

```
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR
```

<img width="82" height="47" alt="image" src="https://github.com/user-attachments/assets/a88fce92-e4bd-48f7-bb66-f08748ca47f9" />

```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound
upper_bound
```

<img width="61" height="30" alt="image" src="https://github.com/user-attachments/assets/69fbd84d-35d8-4379-8b38-da67a7895866" />

```
outliers = [x for x in age if x < lower_bound or x > upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower bound:",lower_bound)
print("Upper bound:",upper_bound)
print("Outliers:",outliers)
```

<img width="215" height="134" alt="image" src="https://github.com/user-attachments/assets/51cebb77-e8e8-44a9-8fd6-469eb41b4ac6" />

```
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```

<img width="145" height="481" alt="image" src="https://github.com/user-attachments/assets/035edb8a-664e-4c7a-b2f6-25c0b6ed1a65" />

```
af.dropna()
```

<img width="166" height="338" alt="image" src="https://github.com/user-attachments/assets/5169ffe7-0993-453a-b9ae-2ed9c56dd6fe" />

```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print("mean of the dataset is",mean)
print("std.deviation is",std)
```

<img width="367" height="50" alt="image" src="https://github.com/user-attachments/assets/f13fcc57-ef60-40a9-8780-366c4988daa2" />

```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z > threshold:
    outlier.append(i)
print("outlier in dataset is",outlier)
```

<img width="227" height="38" alt="image" src="https://github.com/user-attachments/assets/16c07897-d20e-419c-90a3-9d1967d8e10f" />

```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```

<img width="89" height="433" alt="image" src="https://github.com/user-attachments/assets/41473874-cda0-487f-b61b-6e0fc15fbd75" />

```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```

<img width="94" height="62" alt="image" src="https://github.com/user-attachments/assets/e045b9f1-39cb-45c9-a10f-88cbc32ee493" />

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
