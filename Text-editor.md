# key component of text editor
* Main window
    * title,menu and status bar 
    * The main window doesn’t know how to edit text files, it’s only purpose is to provide an interface to the user
* Text view
This is a separate window that is a child of the main (parent) window.
    * This control’s primary purpose is to display and edit text, but it needs to do other things besides this, such as display scrollbars, process mouse and keyboard input, support drag and drop etc.
* Text Document
The “TextDocument” component is not a visible one, but is used to store and manipulate a text file once it has been loaded into memory.
    * The text object has no concept of windows, mice, drawing or painting. All it knows how to do is manipulate text, and supply text to the edit control when it wants to draw something.
* Disk File
The TextDocument will interface directly with this text file, reading and writing to it when it is time to load or save a new document.

## canonical mode
Also called cooked mode, In this mode, keyboard input is only sent to your program when the user presses Enter. This is useful for many programs: it lets the user type in a line of text, use Backspace to fix errors until they get their input exactly the way they want it, and finally press Enter to send it to the program.

## Rendering editor user interface
his happens at three crucial moments:

* Starting up: We're setting the stage for the user.
* After each keypress: To respond to the user's actions.
* Before exiting: To clean up our workspace and leave a tidy farewell message.

# Unicode 
Unicode! Unicode is an encoding system that solves the space issue of ASCII. Like ASCII, Unicode assigns a unique code, called a code point, to each character.

# Buffer
A Buffer is a common structure that holds everything a text editor needs to modify and display a text file. A View interacts with the Buffer to render it on the screen. In many text editors, you can easily switch from one Buffer to the next, allowing you to open multiple files in parallel
**String in Rust manages internally, using a structure known as a Vector, or Vec. Inside a String, there's a Vec<u8>—a vector of bytes, essentially.**

## Rust addresses common memory management challenges at the compiler level:
* It prevents writing beyond allocated memory.
* It manages pointers carefully to avoid errors like modifying data through one pointer and accessing outdated data with another.
* Rust's ownership model, including Move Semantics, tracks and manages pointers effectively, reducing errors from outdated or conflicting data accesses.

