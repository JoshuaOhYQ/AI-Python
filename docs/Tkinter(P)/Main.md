# Documentation For Tkinter

## Getting Started 

Tkinter is Python’s built-in library for creating Graphical User Interfaces (GUIs). The simplest way to start is by creating a window and displaying a text label.

To begin, we first need to:

- create the main window (often called the "root" or "master"). It is the container that holds everything else.
- tell Tkinter where to put it on the screen using ``.pack()`` method which is a geometry manager that stacks widgets in the windom.
- start the event loop to keep window open and listening for interactions (like clicks or keypresses) using. 

!!! example

    ```py linenums="1"
    from tkinter import * 
    
    # 1. Initialize the main window
    root = Tk() 

    # 2. Creating a Label Widget
    mylabel = Label(root, text="Hello World")

    # 3. Putting it on the screen
    mylabel.pack()

    # 4. Running the application
    root.mainloop()
    ```

## Grid System
Unlike ```.pack()```, which simply stacks widgets, the Grid System allows you to organize your GUI using a two-dimensional table structure consisting of rows and columns. This is the most powerful and flexible geometry manager in Tkinter.

Think of your window as a spreadsheet or a coordinate system:

- Rows run horizontally (starting from 0).
- Columns run vertically (starting from 0).
- If a cell is empty, it takes up zero space.

!!! example 

    ```python linenums="1"
    from tkinter import * 
    
    root = Tk()
    root.title("Grid System Basics")

    # 1. Creating Label Widgets
    mylabel1 = Label(root, text="Hello World")
    mylabel2 = Label(root, text="My name is John")

    # 2. Placing them on the screen using the Grid System
    # row=0, column=0 is the top-left corner
    mylabel1.grid(row=0, column=0)

    # row=1, column=0 places this directly below the first label
    mylabel2.grid(row=1, column=0)

    root.mainloop()
    ```

**Key Rule:**

If you put something in `row=0` and something else in `row=5`, but rows 1-4 are empty, Tkinter will collapse the empty space. It will look the same as putting them in rows 0 and 1.

## Buttons
Buttons are the primary way users interact with your GUI. In Tkinter, a button can trigger a specific function (called a callback) when pressed.

!!! example

    ```py linenums="1"
    from tkinter import * 
    
    root = Tk()

    # 1. Define the function to run when the button is clicked
    def myClick():
        myLabel = Label(root, text="Look I clicked a Button!")
        myLabel.pack()

    # 2. Create the button widget
    # Note: 'command' takes the function name WITHOUT parentheses
    myButton = Button(
        root, 
        text="Click Me!", 
        padx=50, 
        pady=50, 
        command=myClick, 
        fg="blue", 
        bg="red"
    )

    myButton.pack()

    root.mainloop()
    ```

**Important Arguments:**

**State**

- parameter determines if a user can actually interact with the button
- ```state=NORMAL```: The default state. The button is clickable.
- ```state=DISABLED```: The button is greyed out and cannot be clicked.

**Padding**

- controls the "breathing room" around the text inside the button or changes the size of the button relative to its content
- ```padx```: Horizontal padding. It adds space to the left and right of the button text.
- ```pady```: Vertical padding. It adds space to the top and bottom of the button text.

**Colour Styling** 

- using simple string names for colors, or Hex codes
- ```fg``` (Foreground): Changes the color of the text.
- ```bg``` (Background): Changes the color of the button face.


!!! Warning

    When assigning a function to a button using ```command=myClick```, do not include the parentheses ().

    - Correct: ```command=myClick``` (Passes the function itself to be called later).
    - Incorrect: ```command=myClick()``` (Calls the function immediately when the script starts, before the button is even pressed).

    If you need to pass arguments to your function, you'll need to use a ```lambda``` function:

    ```py
    command=lambda: myClick("Argument").
    ```

## Input Fields (Entry Widget)

The ```Entry``` widget is the standard way to accept single-line text input from a user. Whether you are building a login form or a calculator, the ```Entry``` widget is your go-to tool for capturing data.

!!! example 

    ```py linenums="1"
    from tkinter import *

    root = Tk() 
    root.title("Handling User Input")

    # 1. Create the Entry widget
    e = Entry(root, width=50, bg="blue", fg="white", borderwidth=5)
    e.pack()

    # 2. Add default text (Optional)
    # 0 is the index (the very beginning of the box)
    e.insert(0, "Enter Your Name: ")

    def myClick():
        # 3. Use .get() to retrieve the current text
        hello = "Hello " + e.get()
        myLabel = Label(root, text=hello)
        myLabel.pack()

    myButton = Button(root, text="Submit Name", command=myClick)
    myButton.pack()

    root.mainloop()
    ```

**Essential Methods:**

- ```.get()```: This is the most important method. It returns whatever string is currently typed into the box.
- ```.insert(index, string)```: Used to put text into the box programmatically. ```0``` is the start, and ```END``` is a special constant to put text at the very end.

- ```.delete(first, last)```: Removes text. To clear the entire box, use ```e.delete(0, END)```. 


**Other ```Entry()``` Arguments:**

| Argument | Description | Example |
|----------|-------------|---------|
| `width` | Sets the width in **character units** (not pixels). | `width=30` |
| `fg / bg` | Sets the text color (**Foreground**) and the box color (**Background**). | `fg="black", bg="#eeeeee"` |
| `borderwidth` | Defines the thickness of the border around the entry box. | `borderwidth=5` |
| `show` | Replaces visible characters with a specific symbol. **Crucial for passwords.** | `show="*"` |
| `font` | Changes the typeface and size of the input text. | `font=("Arial", 14)` |
| `justify` | Aligns the text inside the box. Options: `LEFT`, `CENTER`, or `RIGHT`. | `justify=CENTER` |
| `state` | Can be `NORMAL`, `DISABLED`, or `READONLY`. | `state="readonly"` |

!!! info "Pro-Tip: Placeholder Logic"
    
    In the example, ```e.insert(0, "Enter Your Name: ")``` acts as a placeholder. However, the user has to manually delete that text before typing. In more advanced apps, you would typically use an Event Binding (like ```<FocusIn>```) to automatically clear the box when the user clicks inside it.

**Common Workflow:**

1. Define the Entry widget.

2. Position it using ```.pack()``` or ```.grid()```.

3. Retrieve the data inside a function using ```.get()``` when a button is clicked.

4. Clear the box using ```.delete(0, END)``` if you want to reset the form.

!!! Question 

    Try to create a basic calculator program that will enable the user to calculate basic arithmetic operations which include +, -, * and / . 

    Sample Code: [Project 1: Basic Calculator Program](https://joshuaohyq.github.io/AI-Python/Tkinter%28P%29/Project1/)



