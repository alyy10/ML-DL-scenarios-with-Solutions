
# Vanishing Gradient Problem and Solutions in Deep Learning

## Scenario
Abigail was the first to join the video conference.

Her team has been advising a company working on a deep-learning model. They've been at a standstill for a while, and Abigail's task is to move things forward.

Just ten minutes into the call, Abigail figured out the problem.

During the training of their network and the backpropagation process, the gradients got smaller until they almost reached zero, leaving the weights in the lower layers unmodified.

Abigail identified this as the vanishing gradient problem. Now all she needs to do is hypothesize about why this is happening.

**Question**: Which of the following could be causing the model to suffer from the vanishing gradient problem?

- The hidden layers of the model use the ReLU activation function.
- The model uses batch normalization.
- The hidden layers of the model use the sigmoid activation function.
- The hidden layers of the model use the tanh activation function.

## Solution

If the gradients of the loss function approach zero, the model will stop learning because the network will stop updating the weights. This phenomenon is known as the Vanishing Gradient Problem, and it's very common when using the sigmoid and tanh activation functions in deep neural networks.

The sigmoid and tanh functions squeeze a large input space into a value between [0..1] and [-1..1], respectively. Therefore, large changes in the input of these functions cause small changes in the output. On top of that, both functions saturate when their input grows extremely large or small. Sigmoid saturates at 0 and 1, tanh saturates at -1 and 1. The derivatives at these extremes are very close to zero.

This is not a problem if we are building a shallow network, but as we add more and more layers using these activation functions, the gradients will eventually become too small, and the network will stop learning.

ReLU, on the other hand, is a way to solve the vanishing gradient problem. ReLU is much less likely to saturate, and its derivative is 1 for values larger than zero. This means that the second choice is an incorrect answer.

Finally, batch normalization is another way to mitigate the vanishing gradient problem. If we normalize the input to a layer using a sigmoid activation function, the values won't reach the edges and will stay around the area where the derivative isn't too small.

## How to Fix the Vanishing Gradients Problem Using ReLU

The vanishing gradients problem is one example of unstable behavior that you may encounter when training a deep neural network.

It describes the situation where a deep multilayer feed-forward network or a recurrent neural network is unable to propagate useful gradient information from the output end of the model back to the layers near the input end of the model.

The result is the general inability of models with many layers to learn on a given dataset, or for models with many layers to prematurely converge to a poor solution.

Many fixes and workarounds have been proposed and investigated, such as alternate weight initialization schemes, unsupervised pre-training, layer-wise training, and variations on gradient descent. Perhaps the most common change is the use of the rectified linear activation function that has become the new default, instead of the hyperbolic tangent activation function.

## Vanishing Gradients Problem

Neural networks are trained using stochastic gradient descent.

This involves first calculating the prediction error made by the model and using the error to estimate a gradient used to update each weight in the network so that less error is made next time. This error gradient is propagated backward through the network from the output layer to the input layer.

It is desirable to train neural networks with many layers, as the addition of more layers increases the capacity of the network, making it capable of learning a large training dataset and efficiently representing more complex mapping functions from inputs to outputs.

A problem with training networks with many layers (e.g. deep neural networks) is that the gradient diminishes dramatically as it is propagated backward through the network. The error may be so small by the time it reaches layers close to the input of the model that it may have very little effect. As such, this problem is referred to as the “vanishing gradients” problem.

Vanishing gradients make it difficult to know which direction the parameters should move to improve the cost function.

In fact, the error gradient can be unstable in deep neural networks and not only vanish, but also explode, where the gradient exponentially increases as it is propagated backward through the network. This is referred to as the “exploding gradient” problem.

The term vanishing gradient refers to the fact that in a feedforward network (FFN) the backpropagated error signal typically decreases (or increases) exponentially as a function of the distance from the final layer.

Vanishing gradients is a particular problem with recurrent neural networks as the update of the network involves unrolling the network for each input time step, in effect creating a very deep network that requires weight updates. A modest recurrent neural network may have 200-to-400 input time steps, resulting conceptually in a very deep network.

The vanishing gradients problem may be manifest in a Multilayer Perceptron by a slow rate of improvement of a model during training and perhaps premature convergence, e.g. continued training does not result in any further improvement. Inspecting the changes to the weights during training, we would see more change (i.e. more learning) occurring in the layers closer to the output layer and less change occurring in the layers close to the input layer.

There are many techniques that can be used to reduce the impact of the vanishing gradients problem for feed-forward neural networks, most notably alternate weight initialization schemes and use of alternate activation functions.

## ML/DL Terms Explained

### Vanishing Gradient Problem
The vanishing gradient problem refers to the phenomenon where gradients, used for updating weights in the backpropagation process, become exceedingly small as they move backward through the layers of the network. As a result, the model fails to learn effectively because the weight updates are too small to improve the network.

### Activation Functions
- **Sigmoid Activation Function**: This function maps input values to an output range between 0 and 1, and has a problem of saturation at the extreme ends of the input domain, causing small gradients.
- **Tanh Activation Function**: Similar to the sigmoid, it maps values to a range between -1 and 1. It also suffers from saturation at the ends, causing gradients to vanish.
- **ReLU Activation Function**: Rectified Linear Units (ReLU) are less likely to saturate because they allow positive values to pass through unchanged and only map negative values to zero. This makes it a preferred choice in deep networks to avoid vanishing gradients.

### Batch Normalization
Batch normalization is a technique to normalize the activations of a network's layers by adjusting and scaling the outputs. This can prevent the vanishing gradient problem by ensuring that the inputs to the activation function are kept within a range that prevents saturation, thereby maintaining useful gradients.

### Stochastic Gradient Descent (SGD)
SGD is an optimization algorithm used to minimize the loss function in neural networks by iteratively adjusting the weights in the direction that reduces the error. It works by computing gradients of the loss with respect to the model's weights and using these gradients to update the weights.

