# Documentation For Tkinter

## Getting Started 

Tkinter is Python’s built-in library for creating Graphical User Interfaces (GUIs). The simplest way to start is by creating a window and displaying a text label.

To begin, we first need to:

- create the main window (often called the "root" or "master"). It is the container that holds everything else.
- tell Tkinter where to put it on the screen using ``.pack()`` method which is a geometry manager that stacks widgets in the windom.
- start the event loop to keep window open and listening for interactions (like clicks or keypresses) using. 

!!! example

    ```py linenums="1"
    from tkinter import * # 1. Initialize the main window
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
    from tkinter import * root = Tk()
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









