### Linear Regression in Python

Just learned a pretty nice knowledge about linear regression. Let me know if you have any question.

### The formula is something like this
![linearregression](https://raw.githubusercontent.com/hungvietdo/images/master/linear.png)




#### Linear Regression in Python

#### Libraries in python:
```python
import pandas as pd
import urllib.request
from urllib.request import urlopen
from urllib.request import Request
```

####Reading a csv file from internet
```python
url = "http://www.cs.odu.edu/~hdo/data/sampledata.txt"
source = urllib.request.urlopen(url)
data = pd.read_csv(source,sep=',', parse_dates=True, header=None)
```

####As the source file does not have header we might need a new header row
```python
df = pd.DataFrame(data)
df.columns = ['Student','Hours','Grade']
```
####And add datatype for that columns
```python
df['Student'] = df ['Student'].astype('object')
df['Hours'] = df ['Hours'].astype('float64')
df['Grade'] = df ['Grade'].str.rstrip('%').astype('float64') / 100
```

####
```python
#set x and y for lrm
xi = df.Hours
y =df.Grade
```

####Some other libraries in python
```python
from numpy import arange,array,ones
from pylab import plot,show
from scipy import stats
```
####Now we can calculate slope (beta), intercept (anpha)
```python
slope, intercept,r_value,p_value,std_err = stats.linregress(xi,y)
```
```python
print('r value', r_value)
print('p_value', p_value)
print('standard deviation', std_err)
```
####The rest is pretty easy
```python
line = slope*xi+intercept
plot(xi,line,'r-',xi,y,'o')
show()
```

####Feel free to fork and enjoy the code!

####Sample data for Linear Regression Model

| Student        | Hours           | Grade  |
| ------------- |:-------------:| -----:|
|	Jack|6|53%	|
|	Anne|7|60%	|
|	Harry|6.5|56%	|
|	Sharon|8|79%	|
|	John|6.6|58%	|
|	James|8.1|85%	|
|	Jill|6.8|70%	|
|	Adam|6.9|56%	|
|	Brandon|7.3|69%	|
|	Brett|6.9|76%	|
|	Brady|8.2|79%	|
|	Charles|7.2|68%	|
|	Darren|7.3|74%	|
|	Dave|5.9|72%	|
|	Dawn|8.6|84%	|
|	Denise|7.4|78%	|
|	Eric|7.6|76%	|
|	Emily|6.8|65%	|
|	Fred|8|92%	|
|	Fran|7.4|80%	|
|	Jane|6.5|65%	|

