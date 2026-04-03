## Basic Calculator Program

Below is the sample code for a basic calculator program:

```py linenums="1"
from tkinter import * # Imports every function and class from the tkinter library

root = Tk() # Creates the main window of the application
root.title("Simple Calculator") # Sets the text that appears in the window title bar

# Creates an input field (Entry) where numbers appear. 
# Width defines size, and borderwidth gives it a 3D effect.
e = Entry(root, width=35, borderwidth="5")

# Places the entry field on a grid. 
# columnspan=3 means it takes up the width of three buttons.
e.grid(row=0, column=0, columnspan=3, padx=10, pady=10) 

# --- FUNCTION DEFINITIONS ---

def button_click(number):
    """Handles digit button presses (0-9)."""
    current = e.get() # Grabs whatever is currently in the entry box
    e.delete(0, END)  # Clears the entry box
    # Puts the old number back and attaches the new number to the end (concatenation)
    e.insert(0, str(current) + str(number))

def button_clear():
    """Clears the entire entry box."""
    e.delete(0, END)

def button_add():
    """Prepares the calculator for addition."""
    first_number = e.get() # Grabs the first number entered
    global f_num           # Creates a global variable to store the first number
    global math            # Creates a global variable to store the operation type
    math = "addition"
    f_num = int(first_number) # Converts the string from the entry box to an integer
    e.delete(0, END)       # Clears the screen for the second number

def button_equal():
    """Performs the math based on the stored 'math' variable."""
    second_number = e.get() # Grabs the new number on the screen
    e.delete(0, END)        # Clears the screen to show the result
    
    # Check which operation was selected and perform the calculation
    if math == "addition":
        e.insert(0, f_num + int(second_number))

    if math == "subtraction":
        e.insert(0, f_num - int(second_number))

    if math == "multiplication":
        e.insert(0, f_num * int(second_number))

    if math == "division":
        e.insert(0, f_num / int(second_number))

# These functions do exactly what button_add does, but for different operations
def button_subtract():
    first_number = e.get()
    global f_num
    global math
    math = "subtraction"
    f_num = int(first_number)
    e.delete(0, END)

def button_multiply():
    first_number = e.get()
    global f_num
    global math
    math = "multiplication"
    f_num = int(first_number)
    e.delete(0, END)

def button_divide():
    first_number = e.get()
    global f_num
    global math
    math = "division"
    f_num = int(first_number)
    e.delete(0, END)

# --- BUTTON DEFINITIONS ---

# 'command=lambda' is used here to pass an argument (the number) to the function.
# Without lambda, the function would run immediately when the program starts.
button_1 = Button(root, text="1", padx=40, pady=20, command=lambda:button_click(1))
button_2 = Button(root, text="2", padx=40, pady=20, command=lambda:button_click(2))
button_3 = Button(root, text="3", padx=40, pady=20, command=lambda:button_click(3))
button_4 = Button(root, text="4", padx=40, pady=20, command=lambda:button_click(4))
button_5 = Button(root, text="5", padx=40, pady=20, command=lambda:button_click(5))
button_6 = Button(root, text="6", padx=40, pady=20, command=lambda:button_click(6))
button_7 = Button(root, text="7", padx=40, pady=20, command=lambda:button_click(7))
button_8 = Button(root, text="8", padx=40, pady=20, command=lambda:button_click(8))
button_9 = Button(root, text="9", padx=40, pady=20, command=lambda:button_click(9))
button_0 = Button(root, text="0", padx=40, pady=20, command=lambda:button_click(0))

# Operational buttons (No lambda needed because they don't take arguments)
button_add = Button(root, text="+", padx=39, pady=20, command=button_add)
button_equal = Button(root, text="=", padx=91, pady=20, command=button_equal)
button_clear = Button(root, text="CLEAR", padx=79, pady=20, command=button_clear)
button_subtract = Button(root, text="-", padx=41, pady=20, command=button_subtract)
button_multiply = Button(root, text="*", padx=40, pady=20, command=button_multiply)
button_divide = Button(root, text="/", padx=41, pady=20, command=button_divide)

# --- PUTTING BUTTONS ON THE SCREEN ---

# Row 1: 1, 2, 3
button_1.grid(row=1, column=0)
button_2.grid(row=1, column=1)
button_3.grid(row=1, column=2)

# Row 2: 4, 5, 6
button_4.grid(row=2, column=0)
button_5.grid(row=2, column=1)
button_6.grid(row=2, column=2)

# Row 3: 7, 8, 9
button_7.grid(row=3, column=0)
button_8.grid(row=3, column=1)
button_9.grid(row=3, column=2)

# Row 4: 0 and the Clear button
button_0.grid(row=4, column=0)
button_clear.grid(row=4, column=1, columnspan=2)

# Row 5: + and =
button_add.grid(row=5, column=0)
button_equal.grid(row=5, column=1, columnspan=2)

# Row 6: -, *, /
button_subtract.grid(row=6, column=0)
button_multiply.grid(row=6, column=1)
button_divide.grid(row=6, column=2)

root.mainloop() # Keeps the window open until you close it manually
```

!!! info 

    - The Lambda Secret: When you see ```command=lambda: button_click(1)```, it’s like telling Python: "Don't run this now; wait until the user clicks it, then run it with this specific number."

    - Global Variables: Using ```global f_num``` is necessary because functions in Python usually can't "remember" data after they finish running. Declaring it global lets the ```button_add``` function save a number that the ```button_equal``` function can use later.

    - Concatenation: In ```button_click```, we use ```str(current) + str(number)```. If you had "1" and clicked "2", it makes "12" (text) rather than adding them to get 3. We only convert them to integers (```int()```) when it's time to do actual math.


