## Image Viewer App

Below is the sample code for the image viewer app:

```py linenums="1"
from tkinter import *
from PIL import ImageTk, Image

root = Tk()
root.title("Learning")
root.iconbitmap("Pic.ico")

# Load image files into memory
my_img1 = ImageTk.PhotoImage(Image.open("images/char.bmp"))
my_img2 = ImageTk.PhotoImage(Image.open("images/boat.bmp"))
my_img3 = ImageTk.PhotoImage(Image.open("images/building.bmp"))
my_img4 = ImageTk.PhotoImage(Image.open("images/chia.jpeg"))
my_img5 = ImageTk.PhotoImage(Image.open("images/hansem.jpg"))

# Store image objects in a list for indexing
image_list = [my_img1, my_img2, my_img3, my_img4, my_img5]

# Initial Status Bar: Creates a Label with a sunken border
# anchor=E pushes text to the East (right side)
status = Label(root, text="Image 1 of " + str(len(image_list)), bd=1, relief=SUNKEN, anchor=E)

# Initial image display
my_label = Label(image=my_img1)
my_label.grid(row=0, column=0, columnspan=3)

def forward(image_number):
    """Updates the display and status bar for the next image."""
    global my_label
    global button_forward
    global button_back
    global status # Access the status bar variable
    
    my_label.grid_forget() # Clear current image
    my_label = Label(image=image_list[image_number - 1]) # Load new image
    
    # Update navigation logic
    button_forward = Button(root, text=">>", command=lambda: forward(image_number + 1))
    button_back = Button(root, text="<<", command=lambda: back(image_number - 1))
    
    if image_number == 5:
        button_forward = Button(root, text=">>", state=DISABLED)
    
    # Redraw images and buttons
    my_label.grid(row=0, column=0, columnspan=3)
    button_back.grid(row=1, column=0)
    button_forward.grid(row=1, column=2)
    
    # Update Status Bar: Create a new label with current count and stretch it across the bottom
    status = Label(root, text="Image " + str(image_number) + " of " + str(len(image_list)), bd=1, relief=SUNKEN, anchor=E)
    # sticky=W+E ensures the status bar stretches from West (left) to East (right)
    status.grid(row=2, column=0, columnspan=3, sticky=W+E)

def back(image_number):
    """Updates the display and status bar for the previous image."""
    global my_label
    global button_forward
    global button_back
    global status
    
    my_label.grid_forget()
    my_label = Label(image=image_list[image_number - 1])
    
    button_forward = Button(root, text=">>", command=lambda: forward(image_number + 1))
    button_back = Button(root, text="<<", command=lambda: back(image_number - 1))
    
    if image_number == 1:
        button_back = Button(root, text="<<", state=DISABLED)
    
    my_label.grid(row=0, column=0, columnspan=3)
    button_back.grid(row=1, column=0)
    button_forward.grid(row=1, column=2)
    
    # Update Status Bar text
    status = Label(root, text="Image " + str(image_number) + " of " + str(len(image_list)), bd=1, relief=SUNKEN, anchor=E)
    status.grid(row=2, column=0, columnspan=3, sticky=W+E)

# Navigation Buttons
button_back = Button(root, text="<<", command=back, state=DISABLED)
button_exit = Button(root, text="Exit Program", command=root.destroy)
button_forward = Button(root, text=">>", command=lambda: forward(2))

# Initial Grid placement
button_back.grid(row=1, column=0)
button_exit.grid(row=1, column=1)
button_forward.grid(row=1, column=2, pady=10)

# Place status bar at the very bottom (row 2)
status.grid(row=2, column=0, columnspan=3, sticky=W+E)

root.mainloop()
```

!!! info 

    - **The List-Based Index System**: Instead of creating a new variable for every image, we store them in a **Python List**. This allows the ```forward``` and ```back``` functions to access any image using an index (e.g., ```image_list[0]```). This is the foundation of scalable GUI design.

    - **Clearing the Slate with ```grid_forget()```**: In Tkinter, if you simply grid a new widget over an old one, the old one stays in memory underneath. ```grid_forget()``` effectively "un-renders" the widget. This is crucial for performance and preventing visual glitches where images overlap.

    - **Dynamic Button Re-definition**: Notice that every time you click "Forward" or "Back," the buttons are actually re-created. We do this to update the ```command=lambda``` argument. By re-defining the button inside the function, we "hardcode" the next logical step into the button's command every time the image changes.

    - **Edge Case Handling (State Management):** To prevent the program from crashing (by trying to access an image index that doesn't exist, like image #6 in a list of 5), we use **Conditional Logic**, which is ```state=DISABLED``` that visually greys out the button and makes it unclickable when the user reaches the boundaries of the image list. 

    - **Additional Visual Styling Using ```relief``` and ```bd```:** To make a Label look like a status bar rather than just text, we use ```bd=1``` which sets the border width to 1 pixel and ```relief=SUNKEN``` which gives the widget a "carved into the window" look, which is a standard design pattern for status indicators at the bottom of an application.

    - **The ```sticky``` property:** In the ```.grid()``` system, a widget usually only takes up as much space as the text inside it. By using ```sticky=W+E```, we tell the status bar to "stick" to both the West (left) and East (right) walls of its container. This stretches the sunken border across the entire width of the app.

    - **Dynamic Progress Tracking:** Instead of hardcoding "1 of 5", we use ```str(len(image_list))``` . 

    - **Status Bar Idea:** In a GUI, the screen only updates when a function is triggered. Every time the ```forward``` or ```back``` functions are called, we calculate the new ```image_number``` and re-draw the ```status``` label. This ensures the information at the bottom stays synchronized with the image being displayed.

 


