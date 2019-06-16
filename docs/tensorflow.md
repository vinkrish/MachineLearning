It is an open source library for numerical computation using data flow graphs.

### Computation Graph

The computation graph is the way TensorFlow represents any model in the real world. In the world of TensorFlow, everything can be modeled as a graph. The **nodes** in a graph are the _computations or operators_ that act upon data, and the **edges** in a graph is basically the _tensors_ of the data that are transformed by flowing through these nodes.

Data within the computation graph are called **tensors**. These are nothing but n-dimensional matrices used to represent massive data sets. TensorFlow graph is a directed-acyclic graph, every edge in the graph has an arrow, i.e it points towards a certain node - this is the direction in which data flows, these edges point forward towards a result. The computational nodes within this graph depend on other nodes to forward a data before it can perform its computation. One node can send its output to multiple nodes or it can receive inputs from multiple nodes; In such a case - the node can perform its computation only after all its inputs are available.

### Unrolling the Graph

We model cyclical dependencies by unrolling the graph. The output of the last node is fed into a copy of this graph. Instead of feeding the output into the first node of the same graph, you feed it into the first node of this copy.

How much you unroll your TensorFlow graph depends on the number of iterations you want to run. Even though TensorFlow models the world as a directed-acyclic graph, when you run multiple iterations, it'll automatically unroll graphs to model cyclic dependencies, which are very common in machine learning.

### Tensor

The cental unit of data in TensorFlow. A tensor consists of a set of primitive values shaped into an array of any number of dimensions. In TensorFlow, data isn’t stored as integers, floats, or strings. These values are encapsulated in an object called a tensor.

```py
import tensorflow as tf

# Create TensorFlow object called hello_constant
hello_constant = tf.constant('Hello World!')

with tf.Session() as sess:
    # Run the tf.constant operation in the session
    output = sess.run(hello_constant)
    print(output)
```

### Session
TensorFlow’s api is built around the idea of a computational graph, a way of visualizing a mathematical process.

TensorFlow consists of the following two components:

- a graph protocol buffer
- a runtime that executes the (distributed) graph

These two components are analogous to Python code and the Python interpreter. Just as the Python interpreter is implemented on multiple hardware platforms to run Python code, TensorFlow can run the graph on multiple hardware platforms, including CPU, GPU, and TPU

### A Quick Look at the tf.estimator API

```py
import tensorflow as tf

# Set up a linear classifier.
classifier = tf.estimator.LinearClassifier(feature_columns)

# Train the model on some example data.
classifier.train(input_fn=train_input_fn, steps=2000)

# Use it to predict.
predictions = classifier.predict(input_fn=predict_input_fn)
```

### Hyperparameters

- **Steps**, which is the total number of training iterations. One step calculates the loss from one batch and uses that value to modify the model's weights once.
- **Batch Size**, which is the number of examples (chosen at random) for a single step. For example, the batch size for SGD is 1.

$$total\,number\,of\,trained\,examples = batch\,size * steps$$