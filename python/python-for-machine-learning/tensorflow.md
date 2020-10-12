# Tensorflow

## Introduction to Tensorflow

* Tensorflow Modules and APIs
  * Python, C++, Go, Java supported![](/assets/TFModuleAndAPIs.png)
* a **declarative** language \(vs. imperative\)
  * use functions to express mathematical modules, use functions as computation units
* a graph-based computation model

### Deep Learning Applications

* Internet
  * autorecommendation \(ad, music\)
  * OCR
  * photo labels
* Machine Translation
* Face Recognition
* Scientific Research
  * patten recognition \(eg. astronomy\)
* System Engineering
  * auto parameter tuning
* Agriculture
  * cow and pig
* medical and clinic

---

## Basics

#### Graph

* Tensorflow create a default graph after importing, all operations will go there by default
  * _tf.get\_default\_graph\(\)_
* You can create own graph and get operations there
  * ```py
    g = tf.Graph()
    with g.as_default():
        pass
    ```
* _tf.rest\_default\_graph\(\)_
* edges 
  * tensors/sparse tensors
* nodes
  * **operations **- computation
  * **variable **- storage
  * **constant **- placeholders

#### Session

* tf.session\(\[target=\], \[graph=\], \[config=\]\) object encapsulates the **environment** in which tf.Operation objects are executed and tf.Tensor objects are evaluated
  * target is execution engine, graph is data flow graph, config is start config
  * _sess.run\(&lt;graph&gt;, \[feed\_dict\]\)_
* \_tf.InteractiveSession\(\) - \_create a session, definitions follow
  * _&lt;graph&gt;.run\(\) _- run the graph
* with tf.Session\(\) as sess:
  * _tf.global\_variable\_initilalizer\(\).run_
    * or s.run\(global vairbale initializer\(\)\)
  * &lt;variable&gt;.eval
* 3 Steps when a session runs
  * get tensors
  * evaluate tensors - tensor.eval, operation.run
  * run session - session.run
* Tensorflow will automatically execute sub-graphs in typological order and distribute computations in different **devices**\(per cpu/gpu/tpu\)
  * nodes - can assign nodes to run on different devices
    * _with tf.device\(&lt;device&gt;\) _- will run on a certain device
  * client -server: the actual execution is the client sends the graph to the server \(C++\) and server distributes to workers

#### Tensor

Basic datatype is tensorflow

#### Inputs

* _tf.placeholder\(&lt;tf datatype&gt;, \(shape\)\)_
  * data type like tf.float32
* _tf.Variable_
  * _tf.get\_variable\(&lt;name&gt;, &lt;shape=&gt;, &lt;dtype=&gt;\)_
  * is a special type of operations, returns a **tensor**
* _tf.constant\(&lt;value&gt;\)_

#### Operations

tf.

* @ - tf.matmul\(\)
* Arithmetic
  * _add/multiply/mod/sin/sqrt/fft/argmin_
* Aggregation
  * reduce\_mean\(x, \[dim\]\)
* List
  * _size/rank/split/reverse/cast/one\_hot/quantize_
* Gradient
  * _clip\_by\_value, clip\_by\_norm, clip\_by\_global\_norm_
* Logical
  * _identity/logical\_and/equal/less/is\_finite/is\_nan_
* Dataflow
  * _enqueue/dequeue/size/take\_gard/apply\_grad_
* Initialization
  * _zeros\_initializer/random\_normal\_initializer/orthogonal\_initializer_
* Neural Network
  * _convolution/pool/bias\_add/softmax/dropout/erosion2d_
  * nn
    * loss functions
    * activation functions
      * sigmoid, softmax
* Layers
  * dense
* Random
  * _random\_normal/random\_shuffle/multinomial/random\_gamma_
* String
  * _string\_to\_hash\_bucket/reduce\_join/substr/encode\_base64_
* Image
  * _encode\_png/resize\_images/rot90/rot90/hsv\_to\_rgb/adjust/gamma_

&lt;variable&gt;.

* _assign_
* _assign\_add_

#### Saver

* [tf.saved\_model.simple\_save](https://www.tensorflow.org/versions/r1.15/api_docs/python/tf/saved_model/simple_save)
* [tf.saved\_model.load](https://www.tensorflow.org/api_docs/python/tf/saved_model/load)

#### Built-In Optimizers

tf.train

![](/assets/TFOptimizers.png)

To use optimizers

* compute\_gradients
* operations on gradients \(eg. clip, weighted\)
* apply\_gradients: apply to variables

or, use optmizer.minimize\(loss, global\_step\) directly

---

# Keras

Provides higher level APIs then the Tensorflow. Support key functionalities to build neural networks fast, [work together with Tensorflow](https://blog.keras.io/keras-as-a-simplified-interface-to-tensorflow-tutorial.html)

### Common functions

model.

* add\(\)
  * add layers
* compile\(\)
* fit\(\)
* save\(\)

model types

* model  = Sequential\(\)

#### layers

from keras import layers

* [Dropout](https://keras.io/layers/core/#dropout): applies dropout
* [Dense](#): fully-connected layer.
* [Flatten](https://keras.io/layers/core/#flatten): flattens the input, does not affect the batch size.
* [Activation](https://keras.io/layers/core/#activation): applies an activation function.
* [LeakyReLU](#): applies leaky relu activation.
* [Conv2D](https://keras.io/layers/convolutional/#conv2d): convolution layer 
  * **filters **: number of output channels;
  * **kernel\_size **: an integer or tuple/list of 2 integers, specifying the width and height of the 2D convolution window;
  * **padding**: padding="same" adds zero padding to the input, so that the output has the same width and height, padding='valid' performs convolution only in locations where kernel and the input fully overlap;
  * **activation**: "relu", "tanh", etc.
  * **input\_shape**: shape of input.
* [MaxPooling2D](https://keras.io/layers/pooling/#maxpooling2d): performs 2D max pooling.

#### Utilities 

Used for data processing

[keras.utils](https://scikit-learn.org/stable/modules/classes.html)

* to\_categorical\(y, num\_classes= None, dtype='float32'\)





