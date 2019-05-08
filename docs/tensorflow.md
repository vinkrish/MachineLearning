### Tensor
In TensorFlow, data isn’t stored as integers, floats, or strings. These values are encapsulated in an object called a tensor.

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