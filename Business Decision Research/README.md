# Data Analyst Project: Business Decision Research

Materi ini terbagi menjadi 2 bagian, teori dan test coding yang masing-masing terdiri dari:

1. Teori 
    Konsep Dasar Data Analytics: Tes ini dimaksudkan untuk menguji pemahaman member tentang data analytics.
2. Coding Test
    - Data preparation test: Tes ini dimaksudkan untuk menguji kemampuan member dalam melakukan ETL data.
    - Data visualization test: Tes ini dimaksudkan untuk menguji kemampuan member dalam hal visualisasi data.
    - Basic Stats Method test: Tes ini dimaksudkan untuk menguji kemampuan member dalam melakukan modeling data menggunakan statistika dasar.

Bahasan dari course ini adalah

1. Convert to datetime format
```
df['First_Transaction'] = pd.to_datetime(df['First_Transaction']/1000, unit='s', origin='1970-01-01')
```
2. Create New Columns based on Conditions
```
df.loc[df['Last_Transaction'] <= '2018-08-01','is_churn'] = True
```
3. Get Year
```
df['Year_First_Transaction'] = df['First_Transaction'].dt.year
```
4. Plot
```
df_year.plot(x='Year_First_Transaction', y='Customer_ID', kind='bar', title='Graph of Customer Acquisition')
sns.pointplot(data = df.groupby(['Product', 'Year_First_Transaction']).mean().reset_index()
```
5. Create pivot table
```
df_piv = df.pivot_table(index='is_churn',
                        columns='Product',
                        values='Customer_ID',
                        aggfunc='count',
                        fill_value=0)

```

6. reindex columns
```
df_piv = df_piv.reindex(columns=plot_product)
```
7. Pie Chart
```
df_piv.plot.pie(subplots=True,
                figsize=(10, 7),
                layout=(-1, 2),
                autopct='%1.0f%%',
                title='Proportion Churn by Product')
```
8. Apply
```
df['Count_Transaction_Group'] = df.apply(func, axis=1)
```

9. Create Data Training and Data Testing
```
from sklearn.model_selection import train_test_split

X = df[feature_columns]
y = LabelEncoder().fit_transform(df['is_churn'])

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.25 , random_state=0)
```

10. Modeling
```
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import confusion_matrix

# Inisiasi model logreg
logreg = LogisticRegression()

# fit the model with data
logreg.fit(np.array(X_train), y_train)
y_pred=logreg.predict(X_test)
```

11. Confusion Matrix
```
cnf_matrix = confusion_matrix(y_test, y_pred)
sns.heatmap(pd.DataFrame(cnf_matrix), annot=True, cmap='YlGnBu', fmt='g')
```

12. Akurasi Model
```
from sklearn.metrics import accuracy_score, precision_score, recall_score 

print('Accuracy :', accuracy_score(y_test, y_pred))
print('Precision:', precision_score(y_test, y_pred, average='micro'))
print('Recall :', recall_score(y_test, y_pred, average='micro'))
```

## Source :
https://academy.dqlab.id/