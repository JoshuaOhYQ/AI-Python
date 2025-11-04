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

We can also generate step response for different step amplitude, for example your step input has a magnitude of A=2. This is done by setting the `stepDataOptions`, there are two parameters there, one being `StepAmplitude` and the other being `InputOffset`. `InputOffset` determines the **initial value of the step response**. By default, if ` stepDataOptions` are not set, the `stepAmplitude` is 1 and `InputOffSet` is 0. 

So, in order to generate the step response of G(s) for input amplitude of A=2 and input offset of 0:

```matlab
A = 2 
figure(2)
step (G, stepDataOptions('InputOffSet',0,'StepAmplitude',A))
```

Once the graph is plotted, we can **right-click > Characteristics** to find out about the transient and steady-state information. 

---

## Computing and Plotting of Poles and Zeros

In order to compute and plot the poles and zeros of the transfer function, we can use the function `pzmap()` followed by `pzplot()` which plots the poles and zeros in s-plane and `sgrid` which shows the s-plane grid. If there are no zeros or poles found, then the value is empty. 

```matlab
[poles,zeros]=pzmap(G)
pzplot(G) 
sgrid 
```
<p align="center">
  <img src="https://github.com/JoshuaOhYQ/AI-Python/blob/1459ec828483e143ffc1a8e7f33a4332543a093a/docs/MATLAB/controlsp/poleszeros.png?raw=true" alt="Poles and Zeros" width="1000">
</p>


- Looking at the figure generated, the radial lines (0.997, 0.99, 0.974, 0.945,…) signify the lines of different damping ratio ζ values.Basically, these lines represent (ζ = 0.997, ζ  = 0.99, ζ  = 0.974, ζ = 0.945,…). 

- At the negative horizontal axis, ζ ≥ 1.0 (overdamped) and at the vertical axis, ζ = 0 (undamped). 

- The circular lines (radius 1, 2, 3, 4,…) show the different values of natural frequency ω<sub>n</sub> .

## Simplification of Transfer Functions

Two or more transfer functions in series can be reduced to be one transfer function by finding the product in MATLAB. For example, if we have $G_{1}(s) = \dfrac{2}{(s+2)}$ and $G_{2}(s) = \dfrac{5}{(s+3)}$, we can compute the simplified transfer function as $G_{total}(s) = G_{1}(s)\, G_{2}(s)$ :

```matlab
num = [2]
den = [1 2] 
G_1 = tf(num,den) 
num = [5]
den = [1 3] 
G_2 = tf(num,den) 
G_total = G_1*G_2 
```

## Analyzing a closed-loop system

We can analyze a feedback (closed-loop) control system in MATLAB by using the `feedback()` function. For instance, consider the followng closed-loop system:

<p align="center">
  <img src="https://github.com/JoshuaOhYQ/AI-Python/blob/main/docs/MATLAB/controlsp/Closed-loop.png?raw=true" alt="Closed-loop" width="500">
</p>








