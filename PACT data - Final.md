

```python
### Import packages to pull csv file from repo for analysis
import requests
import pandas as pd
import numpy as np
from sqlalchemy import create_engine
import matplotlib.pyplot as plt
from urllib.request import urlretrieve
```


```python
### Assign URL to variable: url
url = 'https://raw.githubusercontent.com/BIOF309/group-project-rmndr/master/Family_PACT_Providers_File.csv'
```


```python
### Apply pandas package to read the .csv file: url
df = pd.read_csv(url)
```


```python
### Display the DataFrame in Notebook
df
```


```python
### Display the shape of the DataFrame
print(np.shape(df))
```


```python
### Get information on DataFrame
df.info()
```


```python
### Test ability to manipulate DataFrame by display the last 6 columns of the first 5 rows
test = df.iloc[:,-6:]
test.head(5)
```


```python
### Visualize the DataFrame without conditions
df.plot()
plt.yscale('log')
```


```python
### Plot all columns as subplots
df.plot(subplots=True)
plt.show()
```


```python
### Return the number of entries of zipcodes in the series (column)
df['Provider_Address_Zip'].describe()
```


```python
###  Find all of the unique zipcodes from the DataFrame; assign to zc_array
zc_array = df['Provider_Address_Zip'].unique()
zc_array.shape
```


```python
### Sort the df by zipcode
df.sort_values(by='Provider_Address_Zip')
```


```python
### Parse the data against Provider_Type_Code, Provider_Type_Code_Desc and Provider_Address_Zip
parsed = pd.read_csv(url, index_col=['Provider_Type_Code', 'Provider_Type_Code_Desc','Provider_Address_Zip'])
parsed
```


```python
### sort the parsed data
zc = parsed.sort_values(by='Provider_Address_Zip')
zc
```


```python
### Ask user their zipcode (Attempted to raise a ValueError, but was not successful)
CAzip = int(input('What is your zipcode?: '))
type(CAzip)
```


```python
### Find all rows that contain input CAzip
xs = pd.IndexSlice
row = zc.loc[xs[:,:,CAzip],:]
row
```


```python
### Sort resulting dataframe by Provider_Type_Code
row.sort_values(by='Provider_Type_Code')
```


```python
### Select rows and columns for zipcode to determine the count of unique zipcodes in DataFrame
only_zip = df.loc[:,'Provider_Address_Zip']
uzips = only_zip.unique()
soz = only_zip.sort_values()
pd.value_counts(soz)
```


```python
### Show a crude Histogram - Distribution of providers by zipcode
plt.figure(figsize=(10,10)) # figure size argument 
df['Provider_Address_Zip'].hist(bins=704)
plt.title('Volume of Providers by Zipcode')
```
