# Fictitious Names

### Introduction:

This time you will create a data again 

Special thanks to [Chris Albon](http://chrisalbon.com/) for sharing the dataset and materials.
All the credits to this exercise belongs to him.  

In order to understand about it go [here](https://blog.codinghorror.com/a-visual-explanation-of-sql-joins/).

### Step 1. Import the necessary libraries


```python
import pandas as pd 
import numpy as np 
```

### Step 2. Create the 3 DataFrames based on the following raw data


```python
raw_data_1 = {
        'subject_id': ['1', '2', '3', '4', '5'],
        'first_name': ['Alex', 'Amy', 'Allen', 'Alice', 'Ayoung'], 
        'last_name': ['Anderson', 'Ackerman', 'Ali', 'Aoni', 'Atiches']}

raw_data_2 = {
        'subject_id': ['4', '5', '6', '7', '8'],
        'first_name': ['Billy', 'Brian', 'Bran', 'Bryce', 'Betty'], 
        'last_name': ['Bonder', 'Black', 'Balwner', 'Brice', 'Btisan']}

raw_data_3 = {
        'subject_id': ['1', '2', '3', '4', '5', '7', '8', '9', '10', '11'],
        'test_id': [51, 15, 15, 61, 16, 14, 15, 1, 61, 16]}
```

### Step 3. Assign each to a variable called data1, data2, data3


```python
d1 = pd.DataFrame(raw_data_1, columns = ['subject_id', 'first_name', 'last_name'])
d2 = pd.DataFrame(raw_data_2, columns = ['subject_id', 'first_name', 'last_name'])
d3 = pd.DataFrame(raw_data_3, columns = ['subject_id','test_id'])
```


```python
d1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>subject_id</th>
      <th>first_name</th>
      <th>last_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Alex</td>
      <td>Anderson</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Amy</td>
      <td>Ackerman</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Allen</td>
      <td>Ali</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Alice</td>
      <td>Aoni</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Ayoung</td>
      <td>Atiches</td>
    </tr>
  </tbody>
</table>
</div>




```python
d2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>subject_id</th>
      <th>first_name</th>
      <th>last_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4</td>
      <td>Billy</td>
      <td>Bonder</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>Brian</td>
      <td>Black</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6</td>
      <td>Bran</td>
      <td>Balwner</td>
    </tr>
    <tr>
      <th>3</th>
      <td>7</td>
      <td>Bryce</td>
      <td>Brice</td>
    </tr>
    <tr>
      <th>4</th>
      <td>8</td>
      <td>Betty</td>
      <td>Btisan</td>
    </tr>
  </tbody>
</table>
</div>




```python
d3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>subject_id</th>
      <th>test_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>51</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>15</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>15</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>61</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>16</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>14</td>
    </tr>
    <tr>
      <th>6</th>
      <td>8</td>
      <td>15</td>
    </tr>
    <tr>
      <th>7</th>
      <td>9</td>
      <td>1</td>
    </tr>
    <tr>
      <th>8</th>
      <td>10</td>
      <td>61</td>
    </tr>
    <tr>
      <th>9</th>
      <td>11</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>



### Step 4. Join the two dataframes along rows and assign all_data


```python
ad = pd.concat([d1,d2])
ad 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>subject_id</th>
      <th>first_name</th>
      <th>last_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Alex</td>
      <td>Anderson</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Amy</td>
      <td>Ackerman</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Allen</td>
      <td>Ali</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Alice</td>
      <td>Aoni</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Ayoung</td>
      <td>Atiches</td>
    </tr>
    <tr>
      <th>0</th>
      <td>4</td>
      <td>Billy</td>
      <td>Bonder</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>Brian</td>
      <td>Black</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6</td>
      <td>Bran</td>
      <td>Balwner</td>
    </tr>
    <tr>
      <th>3</th>
      <td>7</td>
      <td>Bryce</td>
      <td>Brice</td>
    </tr>
    <tr>
      <th>4</th>
      <td>8</td>
      <td>Betty</td>
      <td>Btisan</td>
    </tr>
  </tbody>
</table>
</div>




```python
ad.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>subject_id</th>
      <th>first_name</th>
      <th>last_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>8</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>top</th>
      <td>4</td>
      <td>Alex</td>
      <td>Anderson</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



### Step 5. Join the two dataframes along columns and assing to all_data_col


```python
adc = pd.concat([d1,d2], axis=1)
adc
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>subject_id</th>
      <th>first_name</th>
      <th>last_name</th>
      <th>subject_id</th>
      <th>first_name</th>
      <th>last_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Alex</td>
      <td>Anderson</td>
      <td>4</td>
      <td>Billy</td>
      <td>Bonder</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Amy</td>
      <td>Ackerman</td>
      <td>5</td>
      <td>Brian</td>
      <td>Black</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Allen</td>
      <td>Ali</td>
      <td>6</td>
      <td>Bran</td>
      <td>Balwner</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Alice</td>
      <td>Aoni</td>
      <td>7</td>
      <td>Bryce</td>
      <td>Brice</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Ayoung</td>
      <td>Atiches</td>
      <td>8</td>
      <td>Betty</td>
      <td>Btisan</td>
    </tr>
  </tbody>
</table>
</div>



### Step 6. Print data3


```python
d3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>subject_id</th>
      <th>test_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>51</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>15</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>15</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>61</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>16</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>14</td>
    </tr>
    <tr>
      <th>6</th>
      <td>8</td>
      <td>15</td>
    </tr>
    <tr>
      <th>7</th>
      <td>9</td>
      <td>1</td>
    </tr>
    <tr>
      <th>8</th>
      <td>10</td>
      <td>61</td>
    </tr>
    <tr>
      <th>9</th>
      <td>11</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>




```python
d3.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>test_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>26.500000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>22.122136</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>15.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>15.500000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>42.250000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>61.000000</td>
    </tr>
  </tbody>
</table>
</div>



### Step 7. Merge all_data and data3 along the subject_id value


```python
pd.merge(ad, d3, on="subject_id")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>subject_id</th>
      <th>first_name</th>
      <th>last_name</th>
      <th>test_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Alex</td>
      <td>Anderson</td>
      <td>51</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Amy</td>
      <td>Ackerman</td>
      <td>15</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Allen</td>
      <td>Ali</td>
      <td>15</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Alice</td>
      <td>Aoni</td>
      <td>61</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Billy</td>
      <td>Bonder</td>
      <td>61</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Ayoung</td>
      <td>Atiches</td>
      <td>16</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>Brian</td>
      <td>Black</td>
      <td>16</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bryce</td>
      <td>Brice</td>
      <td>14</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Betty</td>
      <td>Btisan</td>
      <td>15</td>
    </tr>
  </tbody>
</table>
</div>



### Step 8. Merge only the data that has the same 'subject_id' on both data1 and data2


```python
pd.merge(d1, d2, on='subject_id', how='inner')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>subject_id</th>
      <th>first_name_x</th>
      <th>last_name_x</th>
      <th>first_name_y</th>
      <th>last_name_y</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4</td>
      <td>Alice</td>
      <td>Aoni</td>
      <td>Billy</td>
      <td>Bonder</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>Ayoung</td>
      <td>Atiches</td>
      <td>Brian</td>
      <td>Black</td>
    </tr>
  </tbody>
</table>
</div>



### Step 9. Merge all values in data1 and data2, with matching records from both sides where available.


```python
pd.merge(d1, d2, on='subject_id', how='outer')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>subject_id</th>
      <th>first_name_x</th>
      <th>last_name_x</th>
      <th>first_name_y</th>
      <th>last_name_y</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Alex</td>
      <td>Anderson</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Amy</td>
      <td>Ackerman</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Allen</td>
      <td>Ali</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Alice</td>
      <td>Aoni</td>
      <td>Billy</td>
      <td>Bonder</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Ayoung</td>
      <td>Atiches</td>
      <td>Brian</td>
      <td>Black</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Bran</td>
      <td>Balwner</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Bryce</td>
      <td>Brice</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Betty</td>
      <td>Btisan</td>
    </tr>
  </tbody>
</table>
</div>


