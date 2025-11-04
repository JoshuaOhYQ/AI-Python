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

After this, the transfer functions in MATLAB are created by the command `tf(num, den)` , so to create the transfer function $G(s) = \dfrac{3}{(s+2)(s+5)}$ , we do this:

$$
\text{den}(s) = (s + 2)(s + 5) = s^2 + 7s + 10
$$


```matlab
num = [3] 
den = [1 7 10]
G = tf(num,den)
```

---

## Generating Step Response

To generate a step response of the transfer function, you may use the `step()` function, for instance running `step(G)` will produce the unit step response of transfer Function G(s). The `figure()` function will generate the graph after the unit step response has been applied to the transfer function. 

```matlab
figure(1) 
step(G)
```
We can also generate step response for different step amplitude, for example your step input has a magnitude of A=2. 






??? success "💡 Show Solution"
    ```matlab
    A = -2;
    ```

---