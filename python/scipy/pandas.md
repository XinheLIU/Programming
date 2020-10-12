# Pandas

---

## Basic Data Structure

#### Creation and Attributes

* pd.Series\(&lt;list&gt;, \[index\]\)
  * Attributes: both object and index have **name** attribute 
* pd.Dataframe\(&lt;ndarray/dictionary/list&gt;, index = &lt;pd.date\_range/list&gt;, columns = \[list\] \)
  * index = pd. MultiIndex.from\_tuples\(&lt;list of tuples&gt;, names = \[names of each layer\]\) : will yield a dataframe with hierarchical indexing
* pd.dtypes - display the dtype of every column
  * float, datetime, category, object...
  * pd.Categorical\(\)
    * pd.get\_dummies\(&lt;categorical data&gt;, prefix\) - create dummy variables

### Manipulation

methods can be chained \( linked all together by .\)

#### Operations

* +-/\* - Operate on values

#### Modify

df.

* [reindex](https://pandas.pydata.org/pandas-docs/version/0.22.0/generated/pandas.DataFrame.reset_index.html)\( index = &lt;index&gt;, columns = &lt;list&gt;\)
* rename\(index =, columns = &lt;func&gt;\)
* shift\(&lt;shift num&gt;\)
* T 
  * transpose
* sort\_index\(\[axis\], \[b\], \[ascending\]\)
* modify values
  * add, radd, sub, rsub, div, rdiv, floordiv, rfloordiv, mul, rmul, pow, rpow

#### Bining

pd

* cut\(&lt;df&gt;, &lt;bins&gt;\)
  * key would be intervals
* qcut

#### View/ Conversion to other types

df.

* copy
* index, columns,
  * returns Index
* values
  * returns Numpy nd-array

#### Indexing and Slicing \(and Add/Modify in place\)

* df.&lt;col name&gt; - select one column
* df\[&lt;col name/ col name list&gt;\] - select a column
* df\[&lt;index range&gt;\] -select a number of rows
* df.filter\(regrex = \[regular expression\]\): search columns whose name matches
* df.**loc**\(\[&lt;index range/index value&gt;, &lt;column list/column name&gt;\] -select by label
  * df.at\[&lt;row pos&gt;,&lt;col pos&gt;\] 
* df.i**loc**\[&lt;row positions&gt;, \[column positions\]\]
  * df.iat\[&lt;row position&gt;, &lt;column position&gt;\]
* df\[ **&lt;logic expression&gt;**\] - logical indexing
  * df\[ &lt;df/col&gt;.isin\(&lt;vals&gt;\]
  * df.drop\_duplicates\(\)
* df.head\(n\), df.tail\(n\)
* df.sample\(frac = \[frac\]/n = \[sample size\]\) :select a fraction of rows randomly
* df.nlargest\(n, 'value'\), df.nsmallest\(n, 'value'\)

##### Random Samples

df.

* take\(&lt;sample func-a random permutation&gt;\)
* sample

### Functions

df.

* apply
* apply\_map

use with lambda functions

#### Windows

df.

* expanding\(\)
* rolling\(\)

#### Operations

df.

* query\(&lt;expr&gt;\)
  * see how an expression is expressed if in Pandas
* stats
  * mean\(\[axis\]\)
  * var, std, skew, kurty
  * mad
* Mathematics
  * sub\(&lt;df&gt;\)
  * cumsum\(\), cummax\(\), cummin\(\), cumprod\(\)
  * rank\(method = \[dense/min/first/max/average\], pct = \[Ture/False\]\)
  * shift\(\[n\]\)
  * pct\_change\(\)
* String Operations
  * str.&lt;oper func&gt;\(\)

summarize

* **is\_unique\(\), unique\(\)**
* .nunique\(\) - counts unique values in each col
* .value\_counts\(\): produce a histogram
* len\(）
* **describe\(\)**
* idx: labels, arg: positions
* argmin, argmax, idxmin, idxmax
* sum\(\), min\(\), max\(\), mean\(\), median\(\), var\(\), std\(\)
* arguments
  * axis, skipna, level 
* count\(\)
* quantile

#### 

---

## Load and Write Data

df.

* to\_csv\(\), 
* read\__csv\(&lt;filename&gt; ,\[args\]\), read\_table\(&lt;file\_name&gt;, \[args\]\)_
  * sep = "\|", ","", "\t"
  * names = names 
  * encoding
* to\_hdf\(\), 
* to\__excel\(\), read\_excel_

pd.

* [read\_csv](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html)
  * nrows
  * chucksize
    * returns in chunckers
  * TextParser
* [to\_csv](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_csv.html)
* ExcelFile
* [read\_excel](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_excel.html)
* [to\_excel](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_excel.html)
* read\_html
* read\_pickle\(\), to\_pickle
  * to binary format
  * other formats
    * bcolz
    * Feather
* HDFSTore
  * returns HDF5 object with dict-like API
    * 2 storage schemas : 'fixed' 'table' - latter slightly slower
    * methods
  * * put
      * select
* to\_hdf
* read\_hdf
* read\_sql\(&lt;command&gt;, &lt;db&gt;\)

---

## Merging and Grouping

[Merge, Join and Concantenate](https://pandas.pydata.org/pandas-docs/stable/user_guide/merging.html)

pd.

* merge
* concat

[Grouping](https://pandas.pydata.org/pandas-docs/stable/user_guide/groupby.html)

pd.

* groupby\(&lt;key&gt;,\[axis\], \[level=index name\],\[as index\],\[group\_keys\]\).\[columns\].&lt;aggregator&gt;
  * keys
    * column name
    * dictionary or series \(mapping\)
      * map column \(row\) name to different values then group by values
    * function
      * eg.len
    * Categorial object
      * eg. ones returned by [pd.cut](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.cut.html)
  * aggregator
    * count, sum, mean, media, sts, var, min, max
    * prod
    * first, last - Non NA Values
    * aggregate\(lambda or list of lambda functions\) or agg\(lambda\)
      * aggregate\(\[\(&lt;func1&gt;,&lt;lambda1&gt;\),\(&lt;func2&gt;,&lt;lambda2&gt;\)
        * give column names when aggregate using lambda
    * **apply **- most general form
      * function is called on each row group from the data frame, then the results are glued together with pandas.concat\(\)
  * as index
    * not allow group keys to be hierarchical indices
  * group\_keys
    * not allow group keys, use as original columns
* looping
  * for \(k1, k2...\), v in &lt;grouped&gt;
* groupby\(&lt;key1&gt;\)\['data1'\]
  * syntactic sugar for df\['data1'\].groupby\(df\['key1'\]\)

### Pivot Table

Special case of groupby

* pd.pivot\_table\(&lt;df&gt;, values=&lt;col name&gt;, index=&lt;cols name&gt;,  columns=\[col to putin\], \[arrgfunc=np.mean\]\)
* _df.pivot\_table\(\[cols fo pivot\],&lt;index=&gt;, \[columns\],\[margins\],\[aggfun=\],\[fill\_value=\],\[drop\_na\]\)_
  * margins=True will include partial total
  * default aggfunc is mean
* [df.pivot](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.pivot.html)\(&lt;cols&gt;,&lt;vals&gt;\)
* [pd.crosstab](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.crosstab.html)
  * special type of pivot table

### Pandas Sql

```py
from pandasql import sqldf

def pysqldf(q):
  return sqldf(q, globals())

q = '''
SELECT * 
FROM df_uk_rain a LEFT JOIN df_right b
ON a.year = b.year
LIMIT 5
'''

pysqldf(q）
```

#### Combine DataSets

df\[df.col.isin\( &lt;a col in another df&gt;\)\],df\[df.col.isin\( &lt;a col in another df&gt;\)\],

* * append\(&lt;rows&gt;, ignore\_index = \[T/F\]\)

---

## Data Preprocessing

### Descriptive

df.

* head\(\), tail\(\)
* info\(\)
* describe\(\)
* isnull.sum\(\), notnull\(\).sum
* plot\(\)
  * plot.hist\(\)
  * plot.scatter\(\)

#### Pandas Data Profiling

```py
import pandas_profiling
pandas_profiling.ProfileReport(df)
```

### Reshaping

* df.stack\(\): compress a level in the data frame's columns \( columns become a level index\)

  * unstack\(\[index level\]\):unstack a index level to column

* pd.melt\(&lt;df&gt;, \[indexes\] \) : columns not in indexes are concated by different value combinations as rows

### Duplication

df.

* duplicated - returns boolean \(duplicated rows\)
  * _\[np.where\(df\_uk\_rain\[\['water\_year', 'rain\_octsep'\]\].duplicated\(\)\)\]_
* drop\_duplicates\(\)

### Outliers

use boxplot and winsorizing

### Missing Data

##### Detection

df.

* [isna](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.isna.html)
* isnull
* notnull

can combine with any\(\)

##### Drop or Imputation

df.

* [dropna](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.dropna.html)
* [fillna](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.fillna.html)\(&lt;method&gt;\)
  * method = 'ffill', method = 'bfill'
* fill with model

```py
# fill with model
clf = KNeighborsClassifier(3, weights='distance')
clf.fit(X_no_nan[['age', 'preMLScore', 'postMLScore']], X_no_nan['gender'])
x_imputed = clf.predict(X_with_nan[['age', 'preMLScore', 'postMLScore']])
X_with_imputed = X.copy()
X_with_imputed.loc[idx_with_nan,'gender'] = x_imputed.reshape(-1, 1)
X_with_imputed
```

### Categorical Data

#### Get Dummies

Converting categorical data to "dummy" or "indicator" matrix

df.

* get\_dummies\(\)
  * returns dummy variables
  * get\_indexer
  * add\_prefix

### Vectorized String

df.str

* contains
* findall\(&lt;pattern&gt;, flag\)
* extract
* cat
* count
* endswith, startswith
* findall, get, isalnum, isalpha, isdecimal, isdigit, islower, isnumeric, isupper
* join, len, lower, upper
* match
* pad
* cetner
* repear
* replace
* split
* strip, lstrip, rstrip

---

## Time-Series Data\(pd. Series\)

df.

* resample\(&lt;arg&gt;\).&lt;func&gt;\(\)
  * aggregators : max, mean....
    * olhc
* rolling\(\).&lt;func&gt; \(apply\)
  * rolling window function
* tz\_localize\(\)
* tz\_convert\(\)
* to\_period\(\)
  * convert to period data
* to\_timestamp\(\)

pd

* to\_datetime\(\)
* date\_range\(\)
* period\_range\(,\[freq\]\)
  * asfreq\(\)

### Categorical Data

* df\[cols\].astype\("category"\)
* df.cat
  * categories\(\)
  * set\_categories\(\)
* df.sort\_values\(by\)

### 



