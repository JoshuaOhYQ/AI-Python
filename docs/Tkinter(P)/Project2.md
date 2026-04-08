## Image Viewer App

Below is the sample code for the image viewer app:

```py linenums="1"
from tkinter import *
from PIL import ImageTk, Image

root = Tk()
root.title("Learning")
root.iconbitmap("Pic.ico") # Sets the window icon

# Load multiple images from the 'images/' subfolder using Pillow
my_img1 = ImageTk.PhotoImage(Image.open("images/char.bmp"))
my_img2 = ImageTk.PhotoImage(Image.open("images/boat.bmp"))
my_img3 = ImageTk.PhotoImage(Image.open("images/building.bmp"))
my_img4 = ImageTk.PhotoImage(Image.open("images/chia.jpeg"))
my_img5 = ImageTk.PhotoImage(Image.open("images/hansem.jpg"))

# Group images into a list for easy access via index
image_list = [my_img1, my_img2, my_img3, my_img4, my_img5]

# Initial setup: display the first image in a Label
my_label = Label(image=my_img1)
# span 3 columns so buttons can sit underneath at columns 0, 1, and 2
my_label.grid(row=0, column=0, columnspan=3)

def forward(image_number):
    """Handles moving to the next image."""
    global my_label
    global button_forward
    global button_back
    
    # Remove the existing image label so the new one doesn't stack on top
    my_label.grid_forget()
    
    # Create a new label with the next image (index is image_number - 1)
    my_label = Label(image=image_list[image_number - 1])
    
    # Update buttons: 'forward' prepares for the next index, 'back' for the previous
    button_forward = Button(root, text=">>", command=lambda: forward(image_number + 1))
    button_back = Button(root, text="<<", command=lambda: back(image_number - 1))
    
    # If we reach the last image (5), disable the forward button
    if image_number == 5:
        button_forward = Button(root, text=">>", state=DISABLED)
    
    # Re-place the updated widgets onto the grid
    my_label.grid(row=0, column=0, columnspan=3)
    button_back.grid(row=1, column=0)
    button_forward.grid(row=1, column=2)

def back(image_number):
    """Handles moving to the previous image."""
    global my_label
    global button_forward
    global button_back
    
    my_label.grid_forget()
    my_label = Label(image=image_list[image_number - 1])
    
    button_forward = Button(root, text=">>", command=lambda: forward(image_number + 1))
    button_back = Button(root, text="<<", command=lambda: back(image_number - 1))
    
    # If we reach the first image (1), disable the back button
    if image_number == 1:
        button_back = Button(root, text="<<", state=DISABLED)
    
    my_label.grid(row=0, column=0, columnspan=3)
    button_back.grid(row=1, column=0)
    button_forward.grid(row=1, column=2)

# Initial button definitions
# The back button starts disabled because we start at image 1
button_back = Button(root, text="<<", command=back, state=DISABLED)
button_exit = Button(root, text="Exit Program", command=root.destroy)
# The forward button starts by pointing to the 2nd image
button_forward = Button(root, text=">>", command=lambda: forward(2))

# Layout buttons on the second row
button_back.grid(row=1, column=0)
button_exit.grid(row=1, column=1)
button_forward.grid(row=1, column=2)

root.mainloop()
```

!!! info 

    - **The List-Based Index System**: Instead of creating a new variable for every image, we store them in a **Python List**. This allows the ```forward``` and ```back``` functions to access any image using an index (e.g., ```image_list[0]```). This is the foundation of scalable GUI design.

    - **Clearing the Slate with ```grid_forget()```**: In Tkinter, if you simply grid a new widget over an old one, the old one stays in memory underneath. ```grid_forget()``` effectively "un-renders" the widget. This is crucial for performance and preventing visual glitches where images overlap.

    - **Dynamic Button Re-definition**: Notice that every time you click "Forward" or "Back," the buttons are actually re-created. We do this to update the ```command=lambda``` argument. By re-defining the button inside the function, we "hardcode" the next logical step into the button's command every time the image changes.

    - **Edge Case Handling (State Management):** To prevent the program from crashing (by trying to access an image index that doesn't exist, like image #6 in a list of 5), we use **Conditional Logic**, which is ```state=DISABLED``` that visually greys out the button and makes it unclickable when the user reaches the boundaries of the image list. 


