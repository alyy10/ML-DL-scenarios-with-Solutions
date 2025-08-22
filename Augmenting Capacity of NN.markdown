# Augmenting Capacity of NN

## Question

Lucy's online pet store has seen a significant increase in customers and product variety.  
The neural network model Lucy's team had implemented showed signs of distress. The problem was easy to identify: the company collected more data and features from a wider range of customers. The current model wasn't utilizing all the available information, leading to underfitting.  
Lucy recognized the need to augment the capacity of her model.  

Which of the following steps can Lucy take to augment the capacity of her neural network model?

## Options

a) Lucy should increase the regularization applied to the model.  
b) Lucy should increase the number of nodes on each layer.  
c) Lucy should raise the learning rate for training the model.  
d) Lucy should increase the number of hidden layers in the neural network.

## Solution

**Correct Options: B and D**

## Explanation

The capacity of a neural network model refers to its ability to fit a wide variety of functions, essentially determining the range or scope of mapping functions it can learn from input to output data. In Lucy's case, the model is underfitting, which occurs when the model has too little capacity to effectively learn the training dataset. This is evident from the increased data and features that the current model isn't utilizing fully. To address underfitting, the model's capacity needs to be increased.

- **Option A: Increase the regularization applied to the model.**  
  This is incorrect. Regularization techniques (e.g., L1/L2 penalties, dropout) are used to reduce model capacity by constraining the weights or preventing the model from learning overly complex patterns. Increasing regularization would make the model simpler, which could exacerbate underfitting rather than alleviate it. It is typically applied to combat overfitting, not underfitting.

- **Option B: Increase the number of nodes on each layer.**  
  This is correct. The number of nodes (or units) in a layer defines the "width" of the network. Adding more nodes increases the model's representational capacity, allowing it to learn more complex mapping functions. A single hidden layer with sufficient nodes can theoretically approximate any mapping function (universal approximation theorem), but in practice, increasing nodes helps the model better capture patterns in the data without underfitting. This directly addresses the issue by giving the model more parameters to work with, enabling it to utilize the additional data and features more effectively.

- **Option C: Raise the learning rate for training the model.**  
  This is incorrect. The learning rate controls the step size during optimization (e.g., in gradient descent), affecting how quickly or stably the model converges during training. A higher learning rate might speed up training or help escape local minima, but it does not inherently increase the model's capacity. In fact, an excessively high learning rate could lead to unstable training or divergence, without changing the model's ability to represent complex functions.

- **Option D: Increase the number of hidden layers in the neural network.**  
  This is correct. The number of layers defines the "depth" of the network. Deeper networks (more layers) provide a shortcut to higher capacity with fewer resources per layer, as they can represent functions of increasing complexity. Modern deep learning techniques allow training such models efficiently. Increasing layers expands the model's ability to learn hierarchical features, which is particularly useful when dealing with more data and features, helping to resolve underfitting by enabling the model to approximate more sophisticated mappings.

In summary, both increasing the number of nodes (width) and layers (depth) directly augment the model's capacity, making options B and D the appropriate steps for Lucy. These changes allow the neural network to better handle the expanded dataset and reduce underfitting, while options A and C either reduce capacity or affect training dynamics without impacting capacity. For practical implementation, Lucy should experiment with these adjustments in a framework like Keras, monitoring for potential overfitting as capacity grows.