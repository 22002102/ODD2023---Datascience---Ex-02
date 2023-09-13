# Ex02-Outlier
# AIM
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them


# Explanation:
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.

# Algorithm:
Step1: Read the given Data.

Step2: Get the information about the data.

Step3: Detect the Outliers using IQR method and Z score.

Step4: Remove the outliers.

Step5: Plot the datas using Box Plot.

# Program:
```

import pandas as pd
import seaborn as sns

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df

sns.boxplot(data=df)
sns.scatterplot(data=df)

q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
iqr

low=q1-1.5*iqr
low

high=q3+1.5*iqr
high

aq=df[((df>=low)&(df<=high))]
aq.dropna()

df=df[((df>=low)&(df<=high))]
df.dropna()

sns.boxplot(data=df)
sns.scatterplot(data=df)

import pandas as pd
import seaborn as sns

af=pd.read_csv("heights.csv")
af
sns.boxplot(data=af)
sns.scatterplot(data=af)

min=af['height'].quantile(0.25)
max=af['height'].quantile(0.75)

max
min
iqr=max-min
iqr

dq=af[((af['height']>=min)&(af['height']<=max))]
dq

low=min-1.5*iqr
low

high=max+1.5*iqr
high

qm=af[((af['height']>=low)&(af['height']<=high))]
qm

import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats

data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df

sns.boxplot(data=df)
sns.scatterplot(data=df)

z=np.abs(stats.zscore(df))
print(df[z['weight']>3])

val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]

out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out
op=d_o(val)
op

 ir=pd.read_csv('iris.csv')
 ir
ir.describe()
sns.boxplot(x='sepal_width',data=ir)

c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid

sns.boxplot(x='sepal_width',data=delid)
```
# OUTPUT

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/e5bb4afc-5d1b-43f3-923f-e267bafb176e)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/81eae569-14d3-42b8-b877-2369512cf329)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/7cf403c2-3d53-409f-a3db-03cf5e117b03)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/b75621c7-a667-4006-b105-f59723f1c428)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/15aa7cf8-78ba-491c-8ee7-b8feec950eee)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/42a86b80-d05b-4197-bd2d-e943d2cbaee6)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/aad58c7f-4d34-4c34-83d5-18770a023e0b)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/78a8f3f4-63bf-4191-818b-8d65aa480647)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/761f79e5-b536-446b-a909-245981f2deaa)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/1f984ace-3ea4-4078-8b12-24d6223b3d90)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/9d4521e5-43dc-4bfd-933f-1b87a8a75c0d)

qq![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/aab770f1-aa21-47cb-982a-fc0baee34296)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/d633b358-aa52-40eb-93ae-9c40d4c12d38)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/2c3a1624-55d2-4993-8d2e-deb96377f6ff)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/90659317-0d82-491a-9ab0-a19e23c0fb12)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/cd62a135-5661-4099-bbda-445ac036edca)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/87a487f5-a77b-4371-ac25-216935eecb06)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/e34b9c99-ee4c-4c96-918d-377d29b9310c)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/839f2e51-ca48-41bd-be58-af408dfc4b24)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/edda6a09-fb5d-40af-a748-cbdb4680db47)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/9ff24bad-00d3-43a9-a911-0ea42f97ea2f)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/a2cd8401-340c-4eb3-af2b-7decc1c17bab)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/0a2b4be8-b69c-423e-af6b-1a90fda0deff)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/0a5f73a5-fb15-47b8-bad3-bd7693761c87)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/89eeed6a-3f8a-45eb-bf1f-eda89ad71fa7)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/4a24238f-6608-4723-8d8b-ffde476541f3)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/e20377af-e562-4083-8bb0-f0e9c00593ad)

![image](https://github.com/22002102/ODD2023---Datascience---Ex-02/assets/119091638/b7426de8-cbdb-44a8-9197-94e90326e47f)

# Result
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.




















