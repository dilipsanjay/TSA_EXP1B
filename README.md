
# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
#  Import the necessary Packages
```
` import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data=pd.read_csv('/content/archive (2).zip')
x=data['Date']
y=data['Close']
plt.xlabel('Date')
plt.ylabel('Close Price')
plt.title('Gold Price')
plt.plot(x,y)
```
# REGULAR DIFFERENCING
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data=pd.read_csv('/content/archive (2).zip')
data3 = data.copy()
data3['diff'] = data3['Close'].diff()
data3 = data3.dropna()
x = data3['Date']
y = data3['diff']
plt.xlabel('Date')
plt.ylabel('Daily Change in Closing Price ')
plt.title('Daily Change in Gold Price Over Time')
plt.plot(x,y)
```
# SEASONAL ADJUSTMENT
```
import pandas as pd
import matplotlib.pyplot as plt

data = pd.read_csv('/content/daily-minimum-temperatures-in-me.csv')

print(data.columns)

data1 = data.copy()

data1['Date'] = pd.to_datetime(data1['Date'])
data1['Daily minimum temperatures'] = pd.to_numeric(data1['Daily minimum temperatures'], errors='coerce')
data1 = data1.dropna()
data1['RollingMean'] = data1['Daily minimum temperatures'].rolling(window=30).mean()
data1['SeasonalAdjustment'] = data1['Daily minimum temperatures'] - data1['RollingMean']



x = data1['Date']
y = data1['SeasonalAdjustment']

plt.xlabel('Date')
plt.ylabel('Adjusted Temperature Deviation (°C)')
plt.title('Seasonal Adjustment of Daily Minimum Temperatures')
plt.plot(x, y)
plt.show()
```
# LOG TRANSFORMATION
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data=pd.read_csv('/content/archive (2).zip')
data['diff'] = data['Close'].diff()
data2 = data[data['diff'] > 0].copy()
data2['log'] = np.log(data2['diff'])
data2['log_diff'] = data2['log']-data2['log'].shift(1)
data2 = data2.dropna()
x = data2['Date']
y = data2['log']
plt.xlabel('Date')
plt.ylabel('Log of Differenced Adjusted Close')
plt.title('Log-Transformed Differenced golg Adjusted  Prices')
plt.plot(x,y)
```
### OUTPUT:
# WITHOUT CONVERTION:
![image](https://github.com/user-attachments/assets/25930586-dd92-426c-8ff8-1b7aca65b8eb)

# REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/45f1c901-a40d-4cc4-a1e4-0d8b4378ded1)

# SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/b1b575f8-714c-4a42-a45e-08966300a9b0)

# LOG TRANSFORMATION:
![image](https://github.com/user-attachments/assets/a007f559-4dc8-46a0-8d58-5d76d2810aa2)



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
