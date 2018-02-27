## Getting Started with Windows Command Prompt



![Capture](/home/baboucarr/Documents/web-programming-101/week-2/images/Capture.PNG)

------

In the olden days before the advent of **Graphical User Interface**  people use to interact with computer through a **Command Line Interface.**  A CLI is a text base window for typing commands and receiving text base outputs.



## Get into the Windows command line

1.  Click start
2. In the Search or Run line, type **cmd** (short for command), and press Enter.

## Understanding the prompt

After following the above steps, the Windows command line should be 
shown (similar to the example below). Typically, Windows starts you at 
your user directory. In the example below, the user is Baboucarr, so our prompt is C:\Users\Baboucarr>. This prompt tells us we are in the C: drive(the default drive letter of the hard drive and currently in the Baboucarr directory, which is a subdirectory of the Users directory.

![Capture](/home/baboucarr/Documents/web-programming-101/week-2/images/Capture.PNG)

------



### Key points

1. MS-DOS and the Windows command line are ***not*** **case sensitive**.
2. When working with a file or directory with a space, surround it in quotes. For example, the directory **My Documents** would be "My Documents" when typed.
3. File names can have a long file name of 255 characters and a 3 character file extension.
4. When a file or directory is deleted in the command line, it is not moved into the Recycle Bin
5. If you need help with any of command type /? after the command.



###  Listing the files

Type **dir** at the prompt to list files in the current directory. You should get an output similar to the example image below



![DIR](/home/baboucarr/Documents/web-programming-101/week-2/images/DIR.PNG)

------



### Moving into a directory

To move into a directory, we use the cd , so to move into the Desktop type **cd desktop** and press enter. 
Once you've moved into a new directory the prompt should change, so in our example, the prompt is now C:\Users\Baboucarr\Desktop>. Now in this desktop directory, see what files are found in this directory by typing the **dir** command again.

![CD](/home/baboucarr/Documents/web-programming-101/week-2/images/CD.PNG)

------

### Understand the files

In the Desktop directory, as shown in the above example, there are 0 
files and 25 directories, representing different file types. In Windows, 
you are familiar with files having icons that help represent the file 
type. In the command line, the same thing is accomplished by the file 
extensions. For example, " posts.txt" is a text file because it has a .txt file extension. Time.mp3 is an MP3 music file and minecraft.exe is an executable file and index.html is a html file.



### Moving back a directory

You learned earlier the cd command can move into a directory. This command also allows you to go back a directory by typing **cd..**
 at the prompt. When this command is typed you'll be moved out of the 
Desktop directory and back into the user directory. If you wanted to 
move back to the root directory typing **cd\** takes you to the C:\> prompt.



![move](/home/baboucarr/Documents/web-programming-101/week-2/images/move.PNG)

------





### Creating a directory

Now with your basic understanding of navigating the command line let's 
start creating new directories. To create a directory in the current 
directory use the **mkdir** command. For example, create a directory called "profile" by typing **mkdir profile** at the prompt. If created successfully you should be returned to the prompt with no error message.

![makedirectory](/home/baboucarr/Documents/web-programming-101/week-2/images/makedirectory.PNG)

------



### Moving and copying a file

Now that we've created a file let's move it into an alternate directory.
 To help make things easier, create another directory for the files. So,
 type **mkdir story** to create a new directory in your current path . After the new directory has been created, use the move command to move any folder in to the  story directory. To do this type **move foldername story**
 at the prompt, if done successfully you should get a message indicated 
the file was moved. You could also substitute the move command for the **copy** command to copy the file instead of moving it.

![move](/home/baboucarr/Documents/web-programming-101/week-2/images/move.PNG)



### Rename a file

After the file has been moved into the story directory, move into that 
directory with the cd command to rename the file. In the story directory 
use the rename command to rename the example file into an alternate name. Type **rename example1 example2** at the prompt to rename the file to example2. 



### Deleting a file

Now that we've had our fun with our new file, delete the file with the del command. Type **del first.html**
 to delete the first.bat file. If successful, you are returned to the 
prompt with no errors and the dir command shows no files in the current 
directory.



### Renaming a directory

Go back one directory to get back into the test directory by using the **cd..**
 command mentioned earlier. Now rename our dir2 directory to something 
else using the same rename command we used earlier. At the prompt, type **rename dir2 hope**
 to rename the directory to hope. After this command has been completed,
 type dir and you should now see one directory called hope.



### Removing a directory

While still in the test directory, remove the hope directory by using the rmdir command. At the prompt, type **rmdir hope** to remove the hope directory.

Tip: If the directory you are trying to remove
 contains any files or directories, you'll receive an error. To prevent 
this error use the /s option. For example, if the hope directory still 
had the first.bat file you would need to type **rmdir /s hope** at the prompt.



### Closing or exiting the command line window

After you are done with the Windows command line, you can type **exit** to close the window.