# MATLAB Notes (Basic-Onramp)

Welcome to my introductory notes on using **MATLAB**.  
These notes summarizes the key concepts, syntax, and examples for quick reference.  


## Exercise 1: Multiplying Numbers

Multiply the numbers **3** and **5** using MATLAB.

```matlab
3 * 5
```

??? success "💡 Show Solution"
    ```matlab
    % Multiply 3 and 5
    result = 3 * 5;
    disp(result);   % Output: 15
    ```

---

## Exercise 2: Creating Variables

You can name your MATLAB variables anything you'd like as long as they:

- Start with a **letter**
- Contain only **letters, numbers, and underscores (`_`)**

### Task  
Create a variable named **A** with the value `-2`.

??? success "💡 Show Solution"
    ```matlab
    % Create variable A
    A = -2;
    ```

---

## Exercise 3: Variable Names are Case Sensitive

Notice that `a` and `A` are different variables in MATLAB.

```matlab
a = 10;   % Example variable
A = -2;   % Different variable
```

---

## Exercise 4: Calculating the Mean of `a` and `A`

Use `a` and `A` to calculate:

\[
\frac{a + A}{2}
\]

Store the result in a variable named **meanAa**.

??? success "💡 Show Solution"
    ```matlab
    % Example variables
    a = 10;
    A = -2;

    % Calculate mean
    meanAa = (a + A) / 2;

    disp(meanAa);   % Output: 4
    ```


