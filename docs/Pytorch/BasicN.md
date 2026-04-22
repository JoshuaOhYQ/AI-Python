# Basic Neural Network Model

To create a neural network in PyTorch, we define a class that inherits from ```nn.Module```. This allows us to leverage PyTorch's built-in engine for backpropagation and parameter management.

## Model Architecture 

The code defines a **Multilayer Perceptron (MLP)**, also known as a "Feed-Forward Neural Network."

```py linenums="1"
import torch
import torch.nn as nn
import torch.nn.functional as F

class Model(nn.Module):
    def __init__(self, in_features=4, h1=8, h2=9, out_features=3):
        super().__init__() # Instantiate our nn.Module
        # Layers
        self.fc1 = nn.Linear(in_features, h1) # Fully Connected 1
        self.fc2 = nn.Linear(h1, h2)          # Fully Connected 2
        self.out = nn.Linear(h2, out_features) # Output Layer
    
    def forward(self, x):
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = self.out(x)
        return x

# Set seed for reproducibility
torch.manual_seed(41)
model = Model()
```
So, basically each ```nn.Linear``` layer represents a set of weights and biases connecting one layer of neurons to the next.

| **Input** | **Type** | **Connections** | **Purpose** |
|----------|-------------|---------|-------------------------------|
| **Input** | ```in_feature``` | 4 neurons | Receives raw data (e.g., Sepal/Petal length/width). |
| **Hidden 1** | ```fc1``` | 4 $\rightarrow$ 8 | Learns initial patterns and features. |
| **Hidden 2** | ```fc2``` | 8 $\rightarrow$ 9 | Learns more complex combinations of features. |
| **Output** | ```out``` | 9 $\rightarrow$ 3 | Predicts the probability for each class (3 flower types). |

## Why Object-Oriented Programming (OOP)

You’ll notice we use a Python Class instead of just a list of functions. This is because a Neural Network is more than just math; it is a **stateful object**.

- **Parameter Tracking:** By inheriting from ```nn.Module```, the class automatically tracks all the weights and biases inside your ```Linear``` layers. When it's time to train, you can simply call ```model.parameters()``` to get everything the optimizer needs to update.

- **Encapsulation:** The ```__init__``` method defines the "anatomy" (the layers), while the ```forward``` method defines the "behavior" (how data flows). This keeps the model logic organized and reusable.

- **GPU Integration:** Because it’s an object, you can move the entire model to a GPU with one command: ```model.to('cuda')```.

## ReLU (Rectified Linear Unit)

In the ```forward``` method, we wrap our layers in ```F.relu()```. If we didn't use ReLU, the entire network—no matter how many layers it had—would just behave like one giant linear equation ($y = mx + b$). Linear equations can only solve simple, straight-line problems.

**ReLU adds "Non-Linearity":**

- **The Math:** $f(x) = \max(0, x)$. It turns negative numbers into zero and keeps positive numbers as they are.
- **The Benefit:** This allows the model to learn complex, curvy patterns in data (like distinguishing between two species of flowers that look very similar).
- **Efficiency:** Unlike older functions (like Sigmoid), ReLU is very fast to calculate and helps prevent the "vanishing gradient" problem, which makes training much faster.

## Other Useful Tips

### Checking the Model 
Once you've created an instance, you can print it to see the structure:

```py
print(model)
```

### Training vs. Evaluation Mode
Later, when you start testing your model, you’ll need to toggle its "mode." This is important because some layers (like Dropout) behave differently during testing.

- ```model.train()```: Preps the model for training.
- ```model.eval()```: Preps the model for testing/inference.


### Check Device

To see if your model is ready for a GPU, you can check the parameters:

```py 
# Check which device the model is on (CPU or CUDA)
print(next(model.parameters()).device)
```







