# Linear Regression
```python
import pandas as pd
import urllib.request
from urllib.request import urlopen
from urllib.request import Request

url = "http://www.cs.odu.edu/~hdo/data/sampledata.txt"

source = urllib.request.urlopen(url)
data = pd.read_csv(source,sep=',', parse_dates=True, header=None)

df = pd.DataFrame(data)
df.columns = ['Student','Hours','Grade']
df['Student'] = df ['Student'].astype('object')
df['Hours'] = df ['Hours'].astype('float64')
df['Grade'] = df ['Grade'].str.rstrip('%').astype('float64') / 100

#set x and y for lrm
xi = df.Hours
y =df.Grade
from numpy import arange,array,ones
from pylab import plot,show
from scipy import stats
slope, intercept,r_value,p_value,std_err = stats.linregress(xi,y)
print('r value', r_value)
print('p_value', p_value)
print('standard deviation', std_err)
line = slope*xi+intercept
plot(xi,line,'r-',xi,y,'o')
show()

```

```python
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
```
