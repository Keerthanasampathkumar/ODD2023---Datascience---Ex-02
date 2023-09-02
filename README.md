# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

## Aim:
TO detect and remove the outliers in the given data set and save the final data.

## Algorithm:
Step 1 Import the required packages(pandas,numpy,scipy)

Step 2 Read the given csv file

Step 3 Convert the file into a dataframe and get information of the data.

Step 4 Remove the non numerical data columns using drop() method.

Step 5 Detect the outliers in the data set using z scores method.

Step 6 Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

Step 7 Check if the outliersare removed from data set using graphical methods.

Step 8 Save the final data set into the file.

Program:
NAME : KEERTHANA S
REG NO : 212222230066
```C
FOR BHP.CSV FILE

import pandas as pd
df=pd.read_csv("/bhp.csv")
df
df.info()
df.shape
import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)]
print(newdata)
newdata=df[(df['price_per_sqft']>=lower) | (df['price_per_sqft']<=upper)]
print(newdata)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

FOR HEIGHT_WEIGHT.CSV FILE

import pandas as pd
df=pd.read_csv("/height_weight.csv")
df
df.info()
df.shape
df.describe()
import seaborn as sns
sns.boxplot(x="height",data=df)
Q1=df['height'].quantile(0.25)
Q3=df['height'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata1=df[(df['height']>=lower) | (df['height']<=upper)]
print(newdata1)
newdata=df[(df['height']>=lower) & (df['height']<=upper)]
print(newdata)
sns.boxplot(x='height',data=newdata1)
```
## OUTPUT:
Original data for bhp.csv file:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/483db17f-65ea-48da-a4eb-565dc13b9f42)

Dataset information:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/628fa0f8-d843-4417-8105-9251ed87542b)

Shape of a data:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/b57a7bf5-dde2-439e-aa37-d7612fd5cf2a)

Box Plot of price_per_sqft column without outliers:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/c1604a39-f8bf-4d40-8976-2b80382747c6)

Removing the outlier for price_per_sqft column by using IRQ :
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/5a544fdd-b038-470d-b007-1a372cb9a28a)
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/efddbd34-cee5-41bd-80a9-ce4045440b3f)

Box Plot of price_per_sqft column after IRQ:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/225fa4c6-ba0a-475d-9fe4-805624dc9f5d)

Removing the outlier for price_per_sqft column by using zscore of 3 :
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/1f4639fe-4d73-4377-a5e6-c7f432871039)

![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/64ec03f8-07e3-4c73-843b-f87876e92eef)

Box Plot of price_per_sqft column after zscore of 3:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/3ad47060-6318-4217-acaf-a8061ee9af33)

Original data of height_weight.csv file for height:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/79c7f351-7080-40c9-ac21-438dde0a6d19)

Dataset information:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/729a31e0-eef9-4e0f-80f4-759ac197acf7)

Shape of a dataset:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/8edcea6d-6b95-4f3b-a713-9a6077f0277a)


Box plot of height column without outlier:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/1e7ad805-3511-4275-abcc-9a5c99f16bdf)

Removing the outlier for height column by using IRQ :
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/6a3fc22d-fcae-487e-8e41-6b8f19c15094)

![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/2c2caeab-deff-4361-9101-87a291146e1e)

Box Plot of height column after IRQ:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/6471fdc3-243e-4af1-963e-715d89549848)

Original data of height_weight.csv file for weight:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/cfc4293d-2a35-443c-a0da-ad23efe533b0)

Dataset information:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/76384c92-af1d-46d5-856b-60f091c06798)

Shape of a dataset:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/2069a380-d230-4e76-b0be-a915316e4306)

Box plot weight column without outlier:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/999ce487-d9f8-4aa0-9053-d5071c5e851c)

Removing the outlier for weight column by using IRQ :
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/2d4495f9-c7e9-4eb8-8b4b-a5874cdb5b2f)

![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/0db57522-f7b7-4aa3-8b57-656dad5ac256)

Box Plot of height column after IRQ:
![image](https://github.com/Keerthanasampathkumar/ODD2023---Datascience---Ex-02/assets/119477890/1e88f828-e589-4123-a4b7-7831b4aded5d)

## Result:
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.

