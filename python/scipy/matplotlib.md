## MatplotLib

### Basic

[MatplotLib and Seaborn](https://towardsdatascience.com/matplotlib-seaborn-basics-2bd7b66dbee2)

#### Matplot Lib API Design

* plotting API - pyplot module
* Library - pylab module \(useful function in Numpy and pyplot\)
* plt.plot\(x1,y1,x2,y2..., &lt;attributes controls&gt;\)
  * plt.bar
  * plt.title\(\), .xlabel\(\),.ylabel\(\)
  * plt.gca\(\) - set axes
    * .setx\_lim\(\), .set\_ylim\(\)
  * plt.figure\(&lt;figsize&gt;,&lt;dpi&gt;
  * attributes control
    * color
      * b,g,m\(megenta\),w....
    * type: 
      * \: solid, 
      * \_: dashed,
      * \_. : dash\_dot
      * , : - dotted, 
      * None-nothing, ' '. "" - nothing\_
    * marker: 
      * o - circle 
      * v -triangle\_down
      * s-square
      * p -pentagon
      * \* -star
      * h-hexagon1
      * +-plut
      * D-diamond
  * plt.xlable\(\), ylable\(\), title\(\), legend\(\[loc\]\)
* subplots
  * plt.subplot\(&lt;nrow&gt;&lt;ncol&gt;&lt;ind&gt;, \[color, maker..\]\) 

**Pyplot Module**: MATLAB-like interfaces

#### MatplotLib\_Utils

* simpleTrainingCurves\(\)
  * to visualize training

#### Pandas Ploting

* &lt;dataframe/data column/ data series&gt;.plot\(\[kind\]\)
  * return to plt directly
  * use plt to set up arguments
    * x, y
    * kind
      * bar, pie
    * subplots = True/False
      * default plot all columns together
  * autopct = &lt;format string&gt;
* &lt;df&gt;.boxplot\(\)
  * 3 idioms returns different things
    * &lt;df&gt;.plot\(kind='hist'\)
    * &lt;df&gt;.plot.hist\(\)
    * &lt;df&gt;.hist\(\)

## Seaborn

* .set\_style\(&lt;style&gt;\)
* displot\(&lt;dist&gt;\), box\_plot\(\), heatmap\(\)

---

## PyLab

## Boken

## Plotly

### 



