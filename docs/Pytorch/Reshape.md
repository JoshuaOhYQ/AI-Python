# Reshaping and Slicing Tensors

In PyTorch, managing the dimensions of your data is a fundamental skill. Whether you are prepping data for a neural network or extracting specific features, you will constantly need to reshape and slice your tensors.

## Basic Reshaping 

The most common way to change the shape of a tensor is using the ```.reshape()``` method.

```py linenums="1"
import torch

# Create a 1D tensor from 0 to 9
my_torch = torch.arange(10)

# Reshape into 2 rows and 5 columns
my_torch = my_torch.reshape(2, 5)
print(my_torch)
```

**The "-1" Shortcut**

If you don't want to do the math for one of the dimensions, you can use ```-1```. PyTorch will automatically calculate the correct value based on the total number of elements.

```py linenums="1"
my_torch2 = torch.arange(15)

# We want 3 rows, let PyTorch figure out the columns
my_torch2 = my_torch2.reshape(3, -1) 
print(my_torch2) # Result will be (3, 5)
```

## View vs. Reshape: What's the Difference?

You will often see ```.view()``` used in older code or specific performance-optimized scripts. While they often produce the same result, their internal behavior differs.

| **Feature** | ```view()``` | ```reshape()``` |
|----------|-------------|---------|
| **Memory** | Always returns a "view" of the original memory. | Returns a view if possible; makes a copy if not. |
| **Contiguity** | SRequires the tensor to be **contiguous** in memory. | Handles both contiguous and non-contiguous tensors. |
| **Safety** | Will throw an error if the tensor isn't contiguous. | "Safe" — it won't crash; it just handles the copy behind the scenes. |

**Constiguous Tensor:** a tensor whose elements are stored in a single, uninterrupted block of memory in the same order they are indexed.

!!! Tip

    When in doubt, use ```.reshape()```. It is the most robust method. Only reach for ```.view()``` if you are in a performance-critical loop and want to guarantee that no memory is being copied.

## Memory Sharing 

Because ```reshape``` (when possible) and ```view``` share the same underlying memory as the original tensor, changing one will change the other.

```py linenums="1"
my_torch5 = torch.arange(10)
my_torch6 = my_torch5.reshape(2, 5)

# Changing the original...
my_torch5[1] = 6666

# ...reflects in the reshaped version!
print(my_torch6)
```

## Slicing and Indexing

Slicing in PyTorch works almost identically to NumPy.

```py linenums="1"
my_torch7 = torch.arange(10)

# Access a single element
print(my_torch7[7]) # Returns tensor(7)

# 2D Slicing
my_torch8 = my_torch7.reshape(5, 2)
# [0, 1]
# [2, 3]
# [4, 5] ...

# Get all rows, but only the second column (index 1)
print(my_torch8[:, 1])

# Get all rows, and all columns from index 1 onwards
print(my_torch8[:, 1:])
```

## Other Tensor Manupulation

### Squeeze and Unsqueeze 
Used to add or remove "singleton" dimensions (dimensions of size 1). This is vital when a model expects a batch dimension (e.g., changing shape ```[3, 224, 224]``` to ```[1, 3, 224, 224]```).

- ```unsqueeze(dim)```: Adds a dimension at the specified index.
- ```squeeze()```: Removes all dimensions of size 1.

### Flatten 
If you need to collapse a multi-dimensional tensor into a single 1D array (common when moving from Convolutional layers to Linear layers), use .```flatten()```.

```py 
# Turns a (5, 2) tensor into a (10,) tensor
flat_tensor = my_torch8.flatten()
```

### Permute and Transpose
While ```reshape``` changes how the data is read, ```permute``` actually reorders the dimensions. This is commonly used to switch between "Channels First" ($C, H, W$) and "Channels Last" ($H, W, C$) formats.

```py 
# Swaps dimension 0 and 1
transposed = my_torch8.transpose(0, 1)
```




