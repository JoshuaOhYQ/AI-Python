# Tensor Math Operations

PyTorch makes mathematical operations on tensors intuitive by supporting standard Python operators, functional calls, and specialized "in-place" methods.

## Element-wise Arithmetic

Most basic operations in PyTorch are **element-wise**, meaning the operation is applied to each corresponding pair of elements in the tensors.

```py linenums="1"
import torch

tensor_a = torch.tensor([1, 2, 3, 4])
tensor_b = torch.tensor([5, 6, 7, 8])

# Addition
print(tensor_a + tensor_b)          # Operator
print(torch.add(tensor_a, tensor_b)) # Function

# Subtraction
print(tensor_b - tensor_a)
print(torch.sub(tensor_b, tensor_a))

# Multiplication
print(tensor_a * tensor_b)
print(torch.mul(tensor_a, tensor_b))

# Division
print(tensor_b / tensor_a)
print(torch.div(tensor_b, tensor_a))

# Remainder (Modulo)
print(tensor_b % tensor_a)
print(torch.remainder(tensor_b, tensor_a))

# Exponents (Power)
print(tensor_a ** tensor_b)
print(torch.pow(tensor_a, tensor_b))
```

## In-Place Operations
One unique feature of PyTorch is in-place operations. These modify the tensor data directly without creating a new tensor object in memory. In PyTorch, any function with an **underscore suffix (_)** is an in-place operation.

| **Type** | **Example** | **Effect** |
|----------|-------------|---------|
| **Standard** | ```tensor_a.add(tensor_b)``` | *Returns a new tensor*; ```tensor_a``` remains unchanged. |
| **In-Place** | ```tensor_a.add_(tensor_b)``` | Modifies ```tensor_a``` directly. No new tensor is created. |

``` py 
# Standard way (Reassignment)
tensor_a = tensor_a.add(tensor_b)

# In-place way (Memory efficient)
tensor_a.add_(tensor_b) 
print(tensor_a)
```
!!! tip

    Use in-place operations carefully, as they can sometimes cause issues with gradient calculations during backpropagation.

## Other Essential Opearations

To really work with Neural Networks, you'll need these three "power-user" categories:

### Reduction Operations
These operations "reduce" the dimensions of a tensor by aggregating values.

- ```torch.sum()```: Adds all elements.
- ```torch.mean()```: Calculates the average (requires float tensors).
- ```torch.max()``` / ```torch.min()```: Finds extreme values.
- ```torch.std()```: Standard deviation.

```py
x = torch.tensor([1.0, 2.0, 3.0])
print(x.sum())  # tensor(6.)
print(x.mean()) # tensor(2.)
```

### Matrix Multiplication
While ```*``` is element-wise, deep learning relies heavily on **Matrix Multiplication (Dot Product)**.

- ```torch.matmul(a, b)``` or the ```@``` operator

```py 
# 2x3 matrix
mat1 = torch.randn(2, 3)
# 3x2 matrix
mat2 = torch.randn(3, 2)

# Result is a 2x2 matrix
result = mat1 @ mat2
```

### Broadcasting
PyTorch can perform operations on tensors of different shapes under certain conditions. This is called **Broadcasting**. If you try to add a single value (scalar) to a large tensor, PyTorch "stretches" the scalar to match the shape of the tensor.

```py
tensor = torch.zeros(2, 2)
# PyTorch treats '5' as a (2, 2) tensor of fives
print(tensor + 5)
```












