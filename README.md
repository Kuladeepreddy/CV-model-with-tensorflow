#CV mmodel with tensorflow
You'll train a neural network to recognize items of clothing from a common dataset called Fashion MNIST. It contains 70,000 items of clothing in 10 different categories. Each item of clothing is in a 28x28 grayscale image.
The Fashion MNIST data is available in the tf.keras.datasets API. Load it like this:
Calling load_data on that object gives you two sets of two lists: training values and testing values, which represent graphics that show clothing items and their labels.
You'll notice that all the values are integers between 0 and 255. When training a neural network, it's easier to treat all values as between 0 and 1, a process called normalization. Fortunately, Python provides an easy way to normalize a list like that without looping.
Now design the model. You'll have three layers. Go through them one-by-one and explore the different types of layers and the parameters used for each.
Sequential defines a sequence of layers in the neural network.
Flatten takes a square and turns it into a one-dimensional vector.
Dense adds a layer of neurons.
Activation functions tell each layer of neurons what to do. There are lots of options, but use these for now:
Relu effectively means that if X is greater than 0 return X, else return 0. It only passes values of 0 or greater to the next layer in the network.
Softmax takes a set of values, and effectively picks the biggest one. For example, if the output of the last layer looks like [0.1, 0.1, 0.05, 0.1, 9.5, 0.1, 0.05, 0.05, 0.05], then it saves you from having to sort for the largest value—it returns [0,0,0,0,1,0,0,0,0].
Now that the model is defined, the next thing to do is build it. Create a model by first compiling it with an optimizer and loss function, then train it on your training data and labels. The goal is to have the model figure out the relationship between the training data and its training labels. Later, you want your model to see data that resembles your training data, then make a prediction about what that data should look like.

Notice the use of metrics= as a parameter, which allows TensorFlow to report on the accuracy of the training by checking the predicted results against the known answers (the labels).
When the model is done training, you will see an accuracy value at the end of the final epoch. It might look something like 0.8926 as above. This tells you that your neural network is about 89% accurate in classifying the training data. In other words, it figured out a pattern match between the image and the labels that worked 89% of the time. Not great, but not bad considering it was only trained for five epochs and done quickly.

How would the model perform on data it hasn't seen? That's why you have the test set. You call model.evaluate and pass in the two sets, and it reports the loss for each. That example returned an accuracy of .8789, meaning it was about 88% accurate. (You might have slightly different values.)

As expected, the model is not as accurate with the unknown data as it was with the data it was trained on! As you learn more about TensorFlow, you'll find ways to improve that.
