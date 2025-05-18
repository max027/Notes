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

