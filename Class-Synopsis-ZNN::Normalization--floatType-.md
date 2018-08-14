```C++
template <class floatType>
struct Normalization
{
	Normalization(std::function<floatType(floatType)> norm, std::function<floatType(floatType)> der);
};
```

### Normalization (std::function<floatType(floatType)> norm, std::function<floatType(floatType)> der)
Initializes the Normalization object with a normalization function and a derivative

## Inbuilt Normalization functions:

### Normalization ZNN::Fermi<floatType>()
Creates a Normalization object that performs the sigmoid function

### Normalization ZNN::Identity<floatType>()
Creates a Normalization object that doesn't normalize. 

f(x) = x
and 
ðf/ðx = 1