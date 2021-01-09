# ce02 Command Line Compilation and Packages

![Approved for: Fall 2020](https://img.shields.io/badge/Approved%20for-Fall%202020-blueviolet)

This exercise is designed to introduce text editors as well as how to compile Java code organized into 
packages on a Unix system.

## Prerequisite Knowledge

* [Emacs Tutorial](https://github.com/cs1302uga/cs1302-tutorials/blob/master/emacs/emacs.md)
* [CSCI 1302 Package Tutorial](https://github.com/cs1302uga/cs1302-tutorials/blob/master/packages.md)
* [Emacs Reference Card](https://www.gnu.org/software/emacs/refcards/pdf/refcard.pdf)

## Course-Specific Learning Outcomes

* **LO1.a:** Navigate and modify files, directories, and permissions in a multi-user Unix-like environment.
* **LO1.c:** Create and modify text files and source code using a powerful terminal-based text editor such as Emacs or Vi.
* **LO1.d:** (Partial) Use shell commands to compile new and existing software solutions that are organized into multi-level 
  packages and have external dependencies.
  
## Questions

In your notes, clearly answer the following questions. These instructions assume that you are 
logged into the nike server.

**NOTE:** For each step, please provide in your notes the full command that you typed to make the related 
action happen along with an explanation of why that command worked. Some commands require multiple options. 
It is important to not only recall what you typed but also why you typed each of them. If done properly, your 
class notes will serve as a helpful study guide for the exam.

## Exercise Steps

### Checkpoint 1 Steps

1. In your home directory on nike create the subdirectory structure seen below. What single 
   command can be used to create all of these directories at once?

   ```
   exercise2
    |--- src
          |--- cs1302
                |--- example
   ```

1. Navigate to the `src` directory. In this example, `src` is the default package directory for source code. 
   Inside of the `src` directory, create a file called `Hello.java`. Within this file, write a Java 
   program to prompt the user for their name, read in their full name and then output `Hello, <user>` with 
   their name instead of `<user>`. Your program should work **without any import statements**. Sure, 
   [this is possible](https://github.com/cs1302uga/cs1302-tutorials/blob/master/packages.md#import-statements)!
   In your notes, write the full line of java code to instantiate a `Scanner` object without importing the class.

1. Compile and run your code directly from the default package. Don't use the `-d` option for `javac`
   in this step. In which directory is the compiled code contained?

   Once you are confident that it is working, remove the _compiled_ (byte) code (not your source code).

1. Move the `Hello.java` file (source code) into the `cs1302.example` package. What two things must be done to 
   accomplish this? Hint: [Named Packages](https://github.com/cs1302uga/cs1302-tutorials/blob/master/packages.md#named-package)

1. For better organization, let's separate the source code from the compiled code. Directly inside 
   the `exercise2` directory, add a subdirectory called `bin`. This directory will be the default 
   package for our compiled code. From within `exercise2`, what is the single command to compile 
   `Hello.java` and place the compiled code into the `bin` directory? Remember to use tab completion
   when typing in Unix to avoid mistakes and save you time!

1. From the `exercise2` directory, what is the single command to run the `Hello` program?

1. From your home directory (not `exercise2`), what is the single command to run the `Hello` 
   program?

1. Execute the `find` command from directly within your `exercise2` directory. If the previous steps were 
   executed correctly, you should see the following output:
   
   ```
   .
   ./src
   ./src/cs1302
   ./src/cs1302/example
   ./src/cs1302/example/Hello.java
   ./bin
   ./bin/cs1302
   ./bin/cs1302/example
   ./bin/cs1302/example/Hello.class
   ```
   
<hr/>

![CP](https://img.shields.io/badge/Just%20Finished%20Checkpoint-1-success?style=for-the-badge)

<hr/>

### Checkpoint 2 Steps

1. Navigate to the `exercise2` folder and add a `cs1302.utility` package directory to your heirarchy. 
   Add a class called `MyMethods` to this package. Add a single, static method to to this class which 
   takes two `int` variables as parameters and returns the maximum of the two as an `int`. What is the 
   exact first line of code in `MyMethods.java`?
   
   **PROTIP** Unless it is specifically stated, it is best to always work from the main exercise directory. 
   For example, while working on the source code for this exercise, you can modify all of the files without 
   leaving the `exercise2` directory by providing the relative path (using tab completion) to the file from 
   the `exercise2` directory. This means you would rarely use the `cd` command while working on an exercise. 
   When Unix beginners overuse the `cd` command, they often find themselves lost in the directory structure
   which can lead to mistakes and, in rare cases, frustration!

1. Assuming your present working directory is still `exercise2`, what is the command to compile 
   `MyMethods.java` and place the byte code in the `bin` directory? Remember, there are no dependencies
   when compiling `MyMethods.java` as it does not depend on any other source code.

   Look in the `bin` directory now that you've compiled both `Hello.java` and `MyMethods.java`. 
   Notice the directory hierarchy that was automatically created.

1. Now, modify your `Hello` class.  Have it print out the maximum of two values input by the 
   user. Use the method from your `MyMethods` utility class. What is the line of code to call this 
   method, assuming you have **no import statements** in `Hello.java`?
  
1. **TRICKY** What is the command to compile the `Hello` class from the `exercise2` directory and place the 
   compiled code into `bin`? Note: there is now a dependency in `Hello.java`. It relies on the code
   from `MyMethods`, so the compiler needs to know where to find that class. 
   Hint: [Setting the Class Path](https://github.com/cs1302uga/cs1302-tutorials/blob/master/packages.md#setting-the-class-path)

1. Now, add the import statement for `MyMethods` in `Hello.java` and replace applicable fully 
   qualified names with simple names. Rerun your code to make sure it is working. From the `exercise2` 
   directory, what is the single command to run the `Hello` program?
   
1. Execute the `find` command from directly within your `exercise2` directory. If the previous steps were 
   executed correctly, you should see the following output:
   
   ```
   .
   ./src
   ./src/cs1302
   ./src/cs1302/example
   ./src/cs1302/example/Hello.java
   ./src/cs1302/utility
   ./src/cs1302/utility/MyMethods.java
   ./bin
   ./bin/cs1302
   ./bin/cs1302/example
   ./bin/cs1302/example/Hello.class
   ./bin/cs1302/utility
   ./bin/cs1302/utility/MyMethods.class
   ```
   
<hr/>

![CP](https://img.shields.io/badge/Just%20Finished%20Checkpoint-2-success?style=for-the-badge)

<hr/>

### Submission Steps

**Each student needs to individually submit their own work.**

1. Create a plain text file called `SUBMISSION.md` directly inside the `exercise2`
   directory with the following information:

   1. Your name and UGA ID number;
   1. Collaborator names, if any; and
   
   Here is an example of the contents of `SUBMISSION.md`.
   
   ```
   1. Sally Smith (811-000-999)
   2. Collaborators: Joe Allen, Stacie Mack
   ```

1. Change directories to the parent of `exercise2` (e.g., `cd ..` from `exercise2`). We will use the 
   `tar` command to combine our directory hierarchy into a single file for backup purposes. 
   To do this, execute the command:
   
   ```
   $ tar -cf exercise2.tar exercise2/
   ```

   Read the manual page for `tar` in section 1 of the manual to learn more about `tar` and its 
   various options.

1. List the contents of your directory and make sure you see `exercise2.tar`. Now, to make sure this
   tar file contains all of the work you just did, list all of its contents with the command:
   
   ```
   $ tar -tf exercise2.tar
   ```

1. Now, to make this file smaller, we will compress it with `gzip`. Execute the command:

   ```
   $ gzip exercise2.tar
   ```

   Read the manual page for `gzip` in section 1 of the manual to learn more about `gzip` and its
   various options.

1. List the contents of your directory and make sure you see `exercise2.tar.gz` instead of 
   `exercise2.tar`. Now, you have a compressed backup of your directory saved in the `.tar.gz file`.
   
1. Use the `submit` command to submit this exercise to `csci-1302`:
   
   ```
   $ submit exercise2 csci-1302
   ```
   
   Read the output of the submit command very carefully. If there is an error while submitting, then it will displayed 
   in that output. Additionally, if successful, the submit command creates a new receipt file in the directory you 
   submitted. The receipt file begins with rec and contains a detailed list of all files that were successfully submitted. 
   Look through the contents of the rec file and always remember to keep that file in case there is an issue with your submission.

   **Note:** You must be on Odin to submit.

<hr/>

![CP](https://img.shields.io/badge/Just%20Finished-Submission-success?style=for-the-badge)

<hr/>

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/) [![License: CC BY-NC 4.0](https://img.shields.io/badge/Instructor%20License-CC%20BY--NC%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc/4.0/)

<small>
Copyright &copy; Michael E. Cotterell, Bradley J. Barnes, and the University of Georgia.
This work is licensed under 
a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public and licensed under
a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a> to instructors at institutions of higher education.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>
