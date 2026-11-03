# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 13/10/2026

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
df["y_diff"] = np.ones(y.shape[0])
for i in range(len(y)-1, 0, -1):
    df.loc[i, "y_diff"] = y[i] - y[i-1]
df.loc[0, "y_diff"] = np.nan
df["y_diff"]
```
```
plt.plot(x, df['y_diff'], color="Red")
plt.xlabel("Date")
plt.ylabel("Volume")
plt.title("Regular Differencing Technique applied on Yahoo Stock Volume")
plt.show()
```
```
df['y_log'] = np.log(y)
df['y_log_diff'] = df['y_log'] - df['y_log'].shift(1)
plt.plot(x, df['y_log'], color="Green")
plt.xlabel("Date")
plt.ylabel("Volume")
plt.title("Log applied on Yahoo Stock Volume")
plt.show()
```
```
plt.plot(x, df['y_log_diff'], color="Green")
plt.xlabel("Date")
plt.ylabel("Volume")
plt.title("Log with Regular Differencing applied on Yahoo Stock Volume")
plt.show()
```
```
from statsmodels.tsa.seasonal import seasonal_decompose

result = seasonal_decompose(y, model='additive', period=12)
df['y_sea_diff'] = result.resid
plt.plot(x, df['y_sea_diff'], color="Green")
plt.xlabel("Date")
plt.ylabel("Volume")
plt.title("Seasonal Differencing applied on Yahoo Stock Volume")
plt.show()
```
```
result2 = seasonal_decompose(df['y_log_diff'].dropna(), model='additive', period=12)
df['y_log_sea_diff'] = result2.resid
plt.plot(x, df['y_log_sea_diff'], color="Green")
plt.xlabel("Date")
plt.ylabel("Volume")
plt.title("Log with Seasonal Differencing applied on Yahoo Stock Volume")
plt.show()
```
### OUTPUT:


REGULAR DIFFERENCING:


<img width="579" height="470" alt="image" src="https://github.com/user-attachments/assets/43b0a5e8-788b-4306-94c4-c20815257800" />


SEASONAL ADJUSTMENT:


<img width="572" height="470" alt="image" src="https://github.com/user-attachments/assets/82c19d76-00bc-4430-b026-0578524c65d8" />

<img width="591" height="455" alt="image" src="https://github.com/user-attachments/assets/5ee0ce8d-09c3-4b70-8763-ab68ce9ba424" />


LOG TRANSFORMATION:


<img width="590" height="455" alt="image" src="https://github.com/user-attachments/assets/f0f8dcca-6a7c-4bc4-9ba9-ae7919d7b3ce" />

<img width="586" height="455" alt="image" src="https://github.com/user-attachments/assets/be7fed43-6673-47a2-b035-fbe45cc190a5" />



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
