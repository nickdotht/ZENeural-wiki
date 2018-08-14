# XOR
## What's XOR?

XOR is a [logic gate](https://en.wikipedia.org/wiki/Logic_gate). 
It stands for Exclusive Or: Only when either one of both inputs are on, the output will be true. 

Truth table:
* 1 XOR 1: 0
* 1 XOR 0: 1
* 0 XOR 1: 1
* 0 XOR 0: 0


### Why use XOR for a neural Network?
XOR is a non-linearly separable problem: you cannot draw one single line to separate the two solutions!
Thus, we need at the very least a Neural Network with one Hidden Layer.

## The basic Network

Let's create a Network like this:
```C++
#include "zeneural/NeuralNetwork.hpp"

class xorWrapper {
public:
    ZNN::NeuralNetwork<double> xorNN;
    xorWrapper() {
        xorNN.setInputLayerSize(2);
        xorNN.addHiddenLayer(10);
        xorNN.setOutputLayerSize(1);
    }
};
```

Our Neural Network expects inputs as std::vector<floatType>. Thus, we have to expand our class with a dataset. In our case, we will use a vector that contains vectors of double.

```C++
class xorWrapper {
        std::vector<std::vector<double>> input{{1, 0}, {0, 1}, {0, 0}, {1, 1}};
        std::vector<std::vector<double>> target{{1}, {1}, {0}, {0}};
}
```

Now we are all set to train our NN! To train it, we give it a std::vector<floatType> of input values and the expected results.

```C++
class xorWrapper {
public:
    void trainNN(size_t iterations) {
        for (size_t i = 0; i < iterations; i++)
        {
            xorNN.train(input[0], target[0]);
            xorNN.train(input[1], target[1]);
            xorNN.train(input[2], target[2]);
            xorNN.train(input[3], target[3]);
        }
    }
};
```

The full class now looks like this:

```C++
class xorWrapper {
        std::vector<std::vector<double>> input{{1, 0}, {0, 1}, {0, 0}, {1, 1}};
        std::vector<std::vector<double>> target{{1}, {1}, {0}, {0}};
public:
    ZNN::NeuralNetwork<double> xorNN;
    xorWrapper() {
        xorNN.setInputLayerSize(2);
        xorNN.addHiddenLayer(10);
        xorNN.setOutputLayerSize(1);
    }

    void trainNN(size_t iterations) {
        for (size_t i = 0; i < iterations; i++)
        {
            xorNN.train(input[0], target[0]);
            xorNN.train(input[1], target[1]);
            xorNN.train(input[2], target[2]);
            xorNN.train(input[3], target[3]);
        }
    }
};
```

We can now use this class like this: 

```C++
int main () {
xorWrapper NN{};
NN.train(100);
/*ask for two numbers and put them into a vector called userInput*/
std::cout << NN.xorNN.guess(userInput)[0];
}
```