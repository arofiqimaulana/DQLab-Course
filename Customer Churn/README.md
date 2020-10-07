# Customer Churn Rate
Churn Rate merupakan persentase pelanggan yang tidak melanjutkan layanannya.

## Exploratory Data Analysis
Exploratory Data Analysis memungkinkan analyst memahami isi data yang digunakan, mulai dari distribusi, frekuensi, korelasi dan lainnya. Pada umumnya EDA dilakukan dengan beberapa cara:
    1. Univariat Analysis — analisis deskriptif dengan satu variabel.
    2. Bivariat Analysis — analisis relasi dengan dua variabel yang biasanya dengan target variabel.
    3. Multivariat Analysis — analisis yang menggunakan lebih dari atau sama dengan tiga variabel.

![](images/fitting%20category.png)

Bahasan dari course ini adalah

1. Create pie chart
```
from matplotlib import pyplot as plt
import numpy as np
#Your codes here
fig = plt.figure()
ax = fig.add_axes([0,0,1,1])
ax.axis('equal')
labels = ['No','Yes']
churn = df_load.Churn.value_counts()
ax.pie(churn, labels=labels, autopct='%.0f%%')
plt.show()
```

2. Barchart
```
#creating bin in chart
numerical_features = ['tenure', 'MonthlyCharges', 'TotalCharges']
fig, ax = plt.subplots(1, 3, figsize=(15, 6))
# Use the following code to plot two overlays of histogram per each numerical_features, use a color of blue and orange, respectively
df_load[df_load.Churn == 'No'][numerical_features].hist(bins=20, color='blue', alpha=0.5, ax=ax)
df_load[df_load.Churn == 'Yes'][numerical_features].hist(bins=20, color='blue', alpha=0.5, ax=ax)
plt.show()
```

```
sns.set(style='darkgrid')
# Your code goes here
fig, ax = plt.subplots(3, 3, figsize=(14, 12))
sns.countplot(data=df_load, x='gender', hue='Churn', ax=ax[0][0])
sns.countplot(data=df_load, x='Partner', hue='Churn', ax=ax[0][1])
sns.countplot(data=df_load, x='SeniorCitizen', hue='Churn', ax=ax[0][2])
sns.countplot(data=df_load, x='PhoneService', hue='Churn', ax=ax[1][0])
sns.countplot(data=df_load, x='StreamingTV', hue='Churn', ax=ax[1][1])
sns.countplot(data=df_load, x='InternetService', hue='Churn', ax=ax[1][2])
sns.countplot(data=df_load, x='PaperlessBilling', hue='Churn', ax=ax[2][0])
plt.tight_layout()
plt.show()
```

3. Drop several columns
```
cleaned_df = df_load.drop(['customerID','UpdatedAt'],axis=1)
```

4. Encoding
```
#Convert all the non-numeric columns to numerical data types
for column in cleaned_df.columns:
    if cleaned_df[column].dtype == np.number: continue
    cleaned_df[column] = LabelEncoder().fit_transform(cleaned_df[column])
print(cleaned_df.describe())
```

5. Create Training and Testing Dataset
```
X = cleaned_df.drop('Churn',axis=1)
y = cleaned_df['Churn']
# Splitting train and test
x_train, x_test, y_train, y_test  = train_test_split(X, y, test_size=0.3, random_state=42)
```
6. Modeling
```
from sklearn.linear_model import LogisticRegression
log_model = LogisticRegression().fit(x_train,y_train)
```

```
from sklearn.ensemble import RandomForestClassifier
rdf_model = RandomForestClassifier().fit(x_train,y_train)
```

```
from sklearn.ensemble import GradientBoostingClassifier
gbt_model = GradientBoostingClassifier().fit(x_train,y_train)
```

7. Model Evaluation
```
from sklearn.metrics import classification_report
# Predict
y_train_pred = log_model.predict(x_train)
# Print classification report
print('Classification Report Testing Model (Logistic Regression):')
print(classification_report(y_train, y_train_pred))
```

```
from sklearn.metrics import confusion_matrix
confusion_matrix_df = pd.DataFrame((confusion_matrix(y_train, y_train_pred)), ('No churn', 'Churn'), ('No churn', 'Churn'))
```


## SOURCE
https://academy.dqlab.id/ 