# Getting started 

## Including the Library

To include the Neural Network copy the /library/header folder into your project folder and include the file NeuralNetwork.hpp into your Source file.

Folder Structure:

```
MyProject>
->zeneural
---->Contents of /library/header
->mySourceFile.cpp
```
mySourceFile.cpp:
```
#include "zeneural/NeuralNetwork.hpp```
.
.
.
```

The entire Library is encapsulated in the Namespace ZNN.

## Basics - what is a Neural Network?

> Artificial neural networks (ANN) or connectionist systems are computing systems vaguely inspired by the biological neural networks that constitute animal brains.[1] Such systems "learn" to perform tasks by considering examples, generally without being programmed with any task-specific rules. For example, in image recognition, they might learn to identify images that contain cats by analyzing example images that have been manually labeled as "cat" or "no cat" and using the results to identify cats in other images. They do this without any prior knowledge about cats, e.g., that they have fur, tails, whiskers and cat-like faces. Instead, they automatically generate identifying characteristics from the learning material that they process. 


[source](https://en.wikipedia.org/wiki/Artificial_neural_network)

Basically, you can see a Neural Network as a mathematical model that learns to improve it's predictive capabilities. Or simpler: You show it examples and tell it what it should output until it becomes better and better at guessing. 

### Basics - How does a Neural Network look like?

A NN consists of different Layers. Each Layer consists of a variable amount of Neurons. 

There are three types of Layers: 
* Input Layers (amount: exactly one)
* Hidden Layers (amount: any positive amount)
* Output Layers (amount: exactly one)

Neurons are linked together by weights. 

![As seen here](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Colored_neural_network.svg/296px-Colored_neural_network.svg.png)

## Basics - Using ZENeural's Neural Network
In order to use the NN, you have got to create an object from class ZNN::NeuralNetwork.
It takes as template argument the Datatype to work with (this means that you can use gmp to make the NN work on super high presicions). 

```
ZNN::NeuralNetwork<double> firstNN{};
```

You can now proceed to add layers to it. You have to do it in the following order: 
1) Input Layer
2) Hidden Layer (s)
3) Output Layer

To add an Input Layer, you use

```
ZNN::NeuralNetwork<floatType>::setInputLayerSize(unsigned int layerSize)
```

To add an Hidden Layer, you use

```
ZNN::NeuralNetwork<floatType>::addHiddenLayer (unsigned int layerSize)
```

To add an Hidden Layer, you use

```
ZNN::NeuralNetwork<floatType>::setOutputLayerSize(unsigned int layerSize)
```

To create a simple Neural Network that can evaluate a XOR, we could use this NN-Structure:

```
ZNN::NeuralNetwork<double> xorNN;
xorNN.setInputLayerSize(2); 
xorNN.addHiddenLayer(4);
xorNN.setInputLayerSize(1);
```

[continue](https://github.com/Wittmaxi/ZENeural/wiki/Tutorial---%232-XOR)