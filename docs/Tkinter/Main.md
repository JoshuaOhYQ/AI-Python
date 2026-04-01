# Documentation For Tkinter

## Getting Started 

Tkinter is Python’s built-in library for creating Graphical User Interfaces (GUIs). The simplest way to start is by creating a window and displaying a text label.

To begin, we first need to:
1. create the main window (often called the "root" or "master"). It is the container that holds everything else.
2. tell Tkinter where to put it on the screen using ``.pack()`` method which is a geometry manager that stacks widgets in the windom.
3. start the event loop to keep window open and listening for interactions (like clicks or keypresses). 

!!! example

    ```py
    from tkinter import * # 1. Initialize the main window
    root = Tk() 

    # 2. Creating a Label Widget
    mylabel = Label(root, text="Hello World")

    # 3. Putting it on the screen
    mylabel.pack()

    # 4. Running the application
    root.mainloop()
    ```

















