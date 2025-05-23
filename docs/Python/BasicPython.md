# Basic Python

## Printing
If you want to print or output something in python, there is different ways of doing it whether it is printing a statement or printing a defined variable(1):
{ .annotate }

1. A variable is a named storage location that holds a value! ✋

!!! example

    === "Printing a statement"

        ``` py
        print("Hello world")
        print("The world is amazing!")
        ```
        Output: 
        ```
        Hello world
        The world is amazing!
        ```

    === "Printing a variable"

        ``` py
        name = "Joshua"
        age = 19
        print(name)
        print(age)
        ```
        Output: 
        ```
        Joshua 
        19
        ```
        
    === "Printing a statement with variables"

        ``` py
        name = "Joshua"
        age = 19
        print(f"Hi there, I am {name} and I am {age} years old!")
        ```
        Output: 
        ```
        Hi there, I am Joshua and I am 19 years old!
        ```

## Comments
If you want to add notes or references for the block or line of code you have just written, you can use comments: 

!!! example

    To insert a comment simply use # follow by the comments u want to add! - 
    ``` py
    #To insert comments 
    print("Hello world") #This will output a statement 
    print("This is an amazing world") #This will output a statement 
    ```
    Output:
    ```
    Hello world 
    This is an amazing world
    ```
    When the code is ran, comments will be ignored as it will not be part of the code! 

## Data types
There are four different data types in python, which are **integers, strings, boolen & float**. If you declare a variable, a specific data type is assigned to it depending on the value of the variable:

!!! example

    === "String"
    
        ``` py
        name = "Mc Donalds"
        print(type(name))
     
        ```
        Output: 
        ```
        Kid
        Hello Kid
        Your favourite food is Burger
        ```

    === "Integers"

        ``` py
        age = 18
        quantity = 9
        print(f"You are {age} years old")
        print(f"You bought {quantity} items")
        ```
        Output: 
        ```
        You are 18 years old 
        You bought 9 items 
        ```
        
    === "Float"

        ``` py
        price = 10.99
        gpa = 3.99
        print(f"The price of the item is ${price}")
        print(f"Your GPA is {gpa}")
        ```
        Output: 
        ```
        The price of the item is $10.99
        Your GPA is 3.99
        ```
        
    === "Boolean"

        ``` py
        is_student = True

        if is_student:
            print("You are a student!")
        else: 
            print("You are not a student!")
        ```
        Output: 
        ```
        You are a student!
        ```

## Typecasting
Typecasting converts a variable from one data type to another. To do this, simply equate the variable to itself and the data type you would like to change to: 

!!! example

    We can convert any variable from its original assigned data type to either **string, integer, float or boolean**. The way Python interprets **string, integer and float** is easy to understand and straightforward, but it is slightly different for **booleans**.    

    === "Strings, integers and float"
    
        ```py
        name = "Mc Donalds"
        age = 106
        gpa = 3.9
        
        #Print the intial data type of the variables:
        print(type(name))
        print(type(age))
        print(type(gpa))

        #What happens after typecasting:
        gpa = int(gpa)
        print(gpa)

        age = float(age)
        print(age)

        age = str(age)
        print(age)
        print(type(age))
        ```
        Output:
        ```
        <class 'str'>
        <class 'int'>
        <class 'float'>
        3
        106.0
        106.0
        <class 'str'>
        ```

    === "Boolean"
       
        ```py
        is_student = True
        print(type(is_student))
        ```
        Output:
        ```
        <class 'bool'>
        ```
        
        For boolean with respect to string, if there is any character assigned to the string variable, then it will output **True**:
    
        ```py
        name = "Mc Donalds"
        name = bool(name) 
        print(name)
        ```
        Output:
        ```
        True
        ```
        
        But if there is no character assigned to the string variable, then it will output **False**:

        ```py
        name = ""
        name = bool(name) 
        print(name)
        ```
        Output:
        ```
        False
        ```    

!!! warning
   
    Different data types are used differently and can only be used specifically, for example arithmetic can only be used for float and integer and not strings:

    === "Strings"

        ```py
        age = 106
        age = str(age)
        age += "1"
        print(age)
        ```
        Output:
        ```
        106.01
        ```

    === "Integers"

        ```py
        age = 106
        age += 1
        print(age)
        ```
        Output:
        ```
        107
        ```

    === "Float"

        ```py
        age = 106
        age = float(age)
        age += 1
        print(age)
        ```
        Output:
        ```
        107.0
        ```

## User input
User input is a function that prompts the user to enter data into the Python program. Once the data have been entered, Python will accept the entered data as a **string**(1):
{ .annotate }

1. This is always the case, even if you entered an integer number or floating point number ❗

!!! example

    === "How it works"

        ``` py
        name = input("What is your name?: ")
        print(f"Hello {name}!")
        ```
        Output: 
        ```
        What is your name?: John 
        Hello John!
        ```

    === "Typecasting user input"

        Since the original user input data type is always a string, if you would like to change the data type of that user input, simply enclose the input function with the type cast function:
        
        ``` py
        age = int(input("How old are you?: "))
        age += 1
        print(f"You are {age} years old!")
        ```
        Output: 
        ```
        How old are you?: 30
        You are 31 years old!
        ```



## Basic Arithmetic
For basic arithmetic calculations, symbols such as **(+), (-), (*), (/)** can be used. Other operators include the **modulus operator (%)**, where the remainder of the operand is the resultant and we also have __power (**)__. There are many other useful functions such as __round function, absolute value function, power exponent function, maximum function, minimum function__ and more. 

!!! example "Arithmetic Operators" 

    === "Addition (+)"

        ```py
        a = 5 + 3
        print(a)  
        ```

        Output:

        ```
        8
        ```

    === "Subtraction (-)"

        ```py
        a = 10 - 4
        print(a)  
        ```

        Output:

        ```
        6
        ```

    === "Multiplication (*)"

        ```py
        a = 6 * 7
        print(a)  
        ```

        Output:

        ```
        42
        ```

    === "Division (/)"

        ```py
        a = 10 / 2
        print(a)  #(Always returns float)
        ```

        Output:

        ```
        5.0
        ```

    === "Floor Division (//)"

        ```py
        a = 10 // 3
        print(a)  #(drops the decimal part)
        ```

        Output:

        ```
        3
        ```  

    === "Modulus / Remainder (%)"

        ```py
        a = 10 % 3
        print(a)  #(remainder of the division)
        ```

        Output:

        ```
        1
        ```  

    === "Exponentiation (**)"

        ```py
        a = 2 ** 3
        print(a)  #(2 to the power of 3)
        ```

        Output:

        ```
        8
        ```  

!!! example "Built-in Functions" 

    === "```round(number, [ndigits])```"

        Rounds a number to the nearest integer or to a given number of decimal places.

        ```py
        print(round(3.456))      # 3
        print(round(3.456, 2))   # 3.46

        ```

        Output:

        ```
        3
        3.46
        ```

    === "```abs(number)```"

        Returns the absolute (positive) value.

        ```py
        print(abs(-7))           # 7
        ```

        Output:

        ```
        7
        ```

    === "```pow(x, y)```"

        Raises ```x``` to the power ```y``` (same as ```x ** y```)

        ```py
        print(pow(2, 3))         # 8
        ```

        Output:

        ```
        8
        ```

    === "```max(a, b, ...)```"

        Returns the largest of the arguments.

        ```py
        print(max(3, 9, 1))      # 9
        ```

        Output:

        ```
        9
        ```

    === "```min(a, b, ...)```"

        Returns the smallest of the arguments.

        ```py
        print(min(3, 9, 1))      # 1
        ```

        Output:

        ```
        1
        ```  






