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
    import pandas as pd
    df=pd.read_csv("C:\\Users\\admin\\Downloads\\Data_set.csv")
    df
<img width="1249" height="444" alt="image" src="https://github.com/user-attachments/assets/58ad2f7e-423a-4a98-a067-e6ca4d064025" />

```
df.head(6)
```

<img width="1256" height="353" alt="image" src="https://github.com/user-attachments/assets/450d036d-ed86-476a-8068-8fe40ac76969" />

```
df.tail(6)
```

<img width="1257" height="242" alt="image" src="https://github.com/user-attachments/assets/77b8a01b-ea35-486b-a680-7764ffd4a4a5" />

```
df.isnull()
```

<img width="1247" height="454" alt="image" src="https://github.com/user-attachments/assets/d87f1737-031b-448f-9cd1-9b3ec9dd4ee9" />

```
df.notnull()
```

<img width="1248" height="460" alt="image" src="https://github.com/user-attachments/assets/4e5abbd1-9006-466a-b67b-91ee4578f72f" />

```
df.isnull().sum()
```

<img width="963" height="244" alt="image" src="https://github.com/user-attachments/assets/a76cb3cb-fe0e-405e-847d-5da06afcae2d" />

```
df.describe()
```

<img width="830" height="307" alt="image" src="https://github.com/user-attachments/assets/08dae09e-3715-472d-b8ad-ed326634d927" />

```
df.iloc[1:6,:7]
```

<img width="1077" height="224" alt="image" src="https://github.com/user-attachments/assets/3677a3ff-5e1b-4a37-b073-04b18ef308c1" />

```
df.info()
```

<img width="675" height="367" alt="image" src="https://github.com/user-attachments/assets/4d9bbc8a-4c65-4d4a-840c-5091c5378fea" />

```
df[df['num_episodes']>20]
```

<img width="1254" height="804" alt="image" src="https://github.com/user-attachments/assets/2cc13a08-ff97-4319-b47b-f29e04520efb" />

```
df['country'].value_counts()
```

<img width="446" height="122" alt="image" src="https://github.com/user-attachments/assets/48c17c3e-5edd-4ffb-9929-7af3e1a43f9e" />

```
df.dropna(axis=0)
```

<img width="1253" height="619" alt="image" src="https://github.com/user-attachments/assets/f534c908-636e-44c1-8df4-f9515926d62b" />

```
df.fillna(0)
```

<img width="1266" height="434" alt="image" src="https://github.com/user-attachments/assets/10436ac6-e6fb-45a8-8a16-2ecd2ab4ffd1" />

```
df.fillna(method='ffill')#forward fill
```

<img width="1229" height="467" alt="image" src="https://github.com/user-attachments/assets/3ca74dbc-73f3-4152-8d27-fc14d7c5977d" />

```
df.fillna(method='bfill')#back fill
```

<img width="1250" height="502" alt="image" src="https://github.com/user-attachments/assets/2bcc2775-104e-435d-b77a-be8813ba5477" />

```
df.interpolate()
```

<img width="1257" height="484" alt="image" src="https://github.com/user-attachments/assets/d950ce56-b77e-49f5-a74f-74bd392476e9" />

# IQR(Inter Quartile Range)

```
ir=pd.read_csv('iris.csv')
ir
```

<img width="628" height="504" alt="image" src="https://github.com/user-attachments/assets/d889af68-e532-43ab-8811-f2fad0b02643" />

```
sns.boxplot(x='sepal_width',data=ir)
```

<img width="815" height="704" alt="image" src="https://github.com/user-attachments/assets/19941550-9602-4c2b-be67-975a1d2c8197" />

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```

<img width="381" height="39" alt="image" src="https://github.com/user-attachments/assets/3c895605-d034-4635-8ea8-0ed80130b3c7" />

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```

<img width="398" height="130" alt="image" src="https://github.com/user-attachments/assets/7f36e61f-a54c-406d-9a66-04a31d0a21ca" />

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```

<img width="778" height="705" alt="image" src="https://github.com/user-attachments/assets/8f04d5c0-72af-4be8-9355-f5bd271cc93b" />

```
sns.boxplot(x='sepal_width',data=delid)
```

<img width="624" height="508" alt="image" src="https://github.com/user-attachments/assets/16ceca45-8937-4f7a-b15f-7162204bb079" />

# Z-Score

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```

```
dataset=pd.read_csv("heights.csv")
dataset
```

<img width="214" height="578" alt="image" src="https://github.com/user-attachments/assets/e8810cfc-af60-4e05-b536-434adc913e5d" />

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```

```
iqr = q3-q1
iqr
```

<img width="221" height="33" alt="image" src="https://github.com/user-attachments/assets/01035136-112b-467d-af71-add3aae52ea1" />

```
low = q1 - 1.5*iqr
low
```

<img width="225" height="23" alt="image" src="https://github.com/user-attachments/assets/3ac2ac1b-f33f-4008-b66d-b4aafc710a52" />

```
high = q3 + 1.5*iqr
high
```

<img width="185" height="38" alt="image" src="https://github.com/user-attachments/assets/134282c9-efd6-4325-83f8-b5243e48add6" />

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

<img width="196" height="496" alt="image" src="https://github.com/user-attachments/assets/efc4005d-7545-4021-9efd-77905f6e7baa" />

```
z = np.abs(stats.zscore(df['height']))
z
```

<img width="345" height="388" alt="image" src="https://github.com/user-attachments/assets/650fe801-8447-4a2f-bdc9-981cf3e8026e" />

```
df1 = df[z<3]
df1
```

<img width="212" height="496" alt="image" src="https://github.com/user-attachments/assets/7961459a-9fd2-42c7-9f04-c3dace19e1ad" />


# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
