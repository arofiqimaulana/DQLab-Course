# Data Science in Telco

Bahasan dari Course ini adalah
1.  Validitas suatu variabel
Menggunakan ``` astype(str).str.match(r'(45\d{9,10})') ``` dapat digunakan untuk matching suatu pattern.

2. Checking Missing Values
```
df_load.isnull().values.any()
df_load['tenure'].isnull().sum()
```

3. Handle Missing Values
```
df_load['tenure'].fillna(11,inplace=True)

for col_name in list(df_load.columns):
    if col_name != 'tenure':
        if df_load[col_name].dtype == np.number:
            df_load[col_name].fillna(df_load[col_name].median(),inplace=True)
```

4. Find and drop duplicate Values
```
df_load.drop_duplicates()
``` 

5. Detect Outlier
```
plt.figure() # 
sns.boxplot(x=df_load['tenure'])
plt.show()
```

6. Handle Outlier
```
# Handling with IQR
Q1 = (df_load[['tenure','MonthlyCharges','TotalCharges']]).quantile(0.25)
Q3 = (df_load[['tenure','MonthlyCharges','TotalCharges']]).quantile(0.75)

IQR = Q3 - Q1
maximum = Q3 + (1.5*IQR)
print('Nilai Maximum dari masing-masing Variable adalah: ')
print(maximum)
minimum = Q1 - (1.5*IQR)
print('\nNilai Minimum dari masing-masing Variable adalah: ')
print(minimum)

more_than = (df_load > maximum)
lower_than = (df_load < minimum)
df_load = df_load.mask(more_than, maximum, axis=1)
df_load = df_load.mask(lower_than, minimum, axis=1)

print('\nPersebaran data setelah ditangani Outlier: ')
print(df_load[['tenure','MonthlyCharges','TotalCharges']].describe())
```

7. Find unstandard category values
```
df_load[col_name].value_counts()
```

8. Standardize category values
```
df_load = df_load.replace(['Wanita','Laki-Laki','Churn','Iya'],['Female','Male','Yes','Yes'])
```

### SOURCE : 
https://academy.dqlab.id/