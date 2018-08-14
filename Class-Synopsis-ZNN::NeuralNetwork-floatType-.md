```C++
template <class floatType = double>
class NeuralNetwork
{
  public:
	void setInputLayerSize(unsigned int size);
	void setOutputLayerSize(unsigned int size);
	void addHiddenLayer(unsigned int layerSize);

	std::vector<floatType> guess(std::vector<floatType> input);
	floatType train(std::vector<floatType> input, std::vector<floatType> target);

	void setLearningRate(floatType learningRate);
	void setNormalization(Normalization<floatType> normalizationObject);
};
```

### `void setInputLayerSize (unsigned int size)`
Sets the size of the Input Layer has got to be executed before setOutputLayerSize

### `void addHiddenLayer (unsigned int size)`
Adds a hidden layer with the given size

### `void setOutputLayerSize (unsigned int size)`
Sets the size of the Output Layer

### `std::vector<floatType> guess (std::vector<floatType> input)`
Performs a Neural Network guess with the given output values. The amount of elements in input must be equal to the size of the Input layers.

### `floatType train (std::vector<floatType input, std::vector<floatType> target)`
Performs the Backpropagation algorithm, returns the total error of the neural network, smaller is better.

### `void setLearningRate (floatType learningRate)`
Sets the learning rate of the backpropagation algorithm.

### `void setNormalization ([Normalization]() normalizationObject)`
Sets the Normalization function of the layers. 