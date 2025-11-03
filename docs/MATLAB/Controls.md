# MATLAB Notes (Basic-Onramp)

Welcome to **Control Systems** using **MATLAB**.  
These notes summarizes the key concepts, syntax, and examples for quick reference.  
*This module requires* **Control System Toolbox** *to be installed in MATLAB*. 


## Creating Transfer Functions

To create, we need to declare the numerator and denominator polynomials by creating two vectors (arrays) `num` and `den`. The number of elements in the array tells the degree of the polynomials:

```matlab
den = [2] %refers to den(s) = 2
den = [3 2] %refers to den(s) = 3s + 2
den = [5 3 7] %refers to den(s) = 5s<sup>2</sup> + 3s + 7
den = [3] %refers to den(s) = 3
den = [2 0] %refers to den(s) = 2s + 0 = 2s



```

??? success "💡 Show Solution"
    ```matlab
    result = 3 * 5;
    disp(result);   % Output: 15
    ```

---

## Exercise 2: Creating Variables

You can name your MATLAB variables anything you'd like as long as they:

- Start with a **letter**
- Contain only **letters, numbers, and underscores (`_`)**


Create a variable named **A** with the value `-2`.

??? success "💡 Show Solution"
    ```matlab
    A = -2;
    ```

---