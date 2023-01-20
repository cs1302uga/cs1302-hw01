# hw01 Command Line Compilation and Packages

![Approved for: Spring 2023](https://img.shields.io/badge/Approved%20for-Spring%202023-magenta)

This homework assignment is designed to provide further practice with command-line text editors as well as compiling Java code organized into 
packages on a Unix system.

## Prerequisite Knowledge

* [Emacs Tutorial](https://github.com/cs1302uga/cs1302-tutorials/blob/alsi/emacs/emacs.md)
* [CSCI 1302 Package Tutorial - Part 1](https://github.com/cs1302uga/cs1302-tutorials/blob/alsi/packages1.md)
* [CSCI 1302 Package Tutorial - Part 2](https://github.com/cs1302uga/cs1302-tutorials/blob/alsi/packages2.md)
* [Emacs Reference Card](https://www.gnu.org/software/emacs/refcards/pdf/refcard.pdf)

## Course-Specific Learning Outcomes

* **LO1.a:** Navigate and modify files, directories, and permissions in a multi-user Unix-like environment.
* **LO1.c:** Create and modify text files and source code using a powerful terminal-based text editor such as Emacs or Vi.
* **LO1.d:** (Partial) Use shell commands to compile new and existing software solutions that are organized into multi-level 
  packages and have external dependencies.
  
## Questions

In your notes, clearly answer the questions in the following exercise steps. All instructions assume that you are 
logged into the Odin server.

**NOTE:** For each step, please provide in your notes the full command that you typed to make the related 
action happen along with an explanation of why that command worked. Some commands require multiple options. 
It is important to not only recall what you typed but also why you typed each of them. You won't need to submit your
notes in your final submission. However, if done properly, your exercise notes will serve as a helpful study 
guide for the exam.

## Exercise Steps

### Checkpoint 1 Steps

1. In your home directory on Odin create the subdirectory structure seen below. What single 
   command can be used to create all of these directories at once?

   ```
   homework1
    |--- src
          |--- cs1302
                |--- example
   ```

1. Navigate to the `src` directory. In this example, `src` is the default package directory for source code. 
   Inside of the `src` directory, create a file called `Hello.java`. Within this file, write a Java 
   program to prompt the user for their name, read in their full name and then output `Hello, <user>` with 
   their name instead of `<user>`. <!--Your program should work **without any import statements**. Sure, 
   [this is possible](https://github.com/cs1302uga/cs1302-tutorials/blob/alsi/packages2.md#import-statements)!
   In your notes, write the full line of java code to instantiate a `Scanner` object without importing the class.-->

1. Compile and run your code directly from the default package. Don't use the `-d` option for `javac`
   in this step. In which directory is the compiled code contained?

   Once you are confident that it is working, remove the _compiled_ (byte) code (not your source code).

1. Move the `Hello.java` file (source code) into the `cs1302.example` package. What two things must be done to 
   accomplish this? Hint: [Named Packages](https://github.com/cs1302uga/cs1302-tutorials/blob/alsi/packages1.md#named-package)

1. For better organization, let's separate the source code from the compiled code. Directly inside 
   the `homework1` directory, add a subdirectory called `bin`. This directory will be the default 
   package for our compiled code. From within `homework1`, what is the single command to compile 
   `Hello.java` and place the compiled code into the `bin` directory? Remember to use tab completion
   when typing in Unix to avoid mistakes and save you time!

1. From the `homework1` directory, what is the single command to run the `Hello` program?

1. From your home directory (not `homework1`), what is the single command to run the `Hello` 
   program?

1. Execute the `find` command from directly within your `homework1` directory. If the previous steps were 
   executed correctly, you should see the following output:
   
   **Note:**  If you see any tilda (~) files, those are just backup copies of older versions 
   of your files. You can ignore those.
   
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

1. Navigate to the `homework1` folder and add a `cs1302.utility` package directory to your hierarchy. 
   Add a class called `MyMethods` to this package. Add a single, static method to this class. You can
   give it any valid name you want, but the body of the method should determine and return the bigger of 
   two `int` values supplied as parameters to the method. These values will be supplied when you call the 
   method in a later step. What is the exact first line of code in `MyMethods.java`?
   
   **PROTIP** Unless it is specifically stated, it is best to always work from the main project directory. 
   For example, while working on the source code for this exercise, you can modify all of the files without 
   leaving the `homework1` directory by providing the relative path (using tab completion) to the file from 
   the `homework1` directory. This means you would **rarely use the `cd` command while working on an assignment**. 
   When Unix beginners overuse the `cd` command, they often find themselves lost in the directory structure
   which can lead to mistakes and, in rare cases, frustration!

1. Assuming your present working directory is still `homework1`, what is the command to compile 
   `MyMethods.java` and place the byte code in the `bin` directory? Remember, there are no dependencies
   when compiling `MyMethods.java` as it does not depend on any other source code.

   Look in the `bin` directory now that you've compiled both `Hello.java` and `MyMethods.java`. 
   Notice the directory hierarchy that was automatically created.

1. Now, modify the `Hello` class in the `Hello.java` file. Have it print out the maximum of two values input by the 
   user. To accomplish this, in the `main` method of your `Hello` class, you should read two integers from a valid 
   `Scanner` object and pass those values into the method you created in the `MyMethods` utility class. 
   In other words, you should call the method in `MyMethods` from the `main` method in your `Hello` class and print
   the result.
   What is the line of code to call this method, assuming you have **no import statements** in `Hello.java`?
  
1. **TRICKY** What is the command to compile the `Hello` class from the `homework1` directory and place the 
   compiled code into `bin`? Note: there is now a dependency in `Hello.java`. It relies on the code
   from `MyMethods`, so the compiler needs to know where to find that class. 
   Hint: [Setting the Class Path](https://github.com/cs1302uga/cs1302-tutorials/blob/alsi/packages2.md#setting-the-class-path)

1. Now, add the import statement for `MyMethods` in `Hello.java` and replace applicable fully 
   qualified names with simple names. Rerun your code to make sure it is working. From the `homework1` 
   directory, what is the single command to run the `Hello` program?
   
1. Execute the `find` command from directly within your `homework1` directory. If the previous steps were 
   executed correctly, you should see the following output:
   
   **Note:**  If you see any tilda (~) files, those are just backup copies of older versions 
   of your files. You can ignore those.
   
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

1. Create a plain text file called `SUBMISSION.md` directly inside the `homework1`
   directory with your name and UGA ID number.
   
   Here is an example of the contents of `SUBMISSION.md`.
   
   ```
   Sally Smith (811-000-999)
   ```

1. Change directories to the parent of `homework1` (e.g., `cd ..` from `homework1`). We will use the 
   `tar` command to combine our directory hierarchy into a single file for backup purposes. 
   To do this, execute the command:
   
   ```
   $ tar -cf homework1.tar homework1/
   ```

   Read the manual page for `tar` in section 1 of the manual to learn more about `tar` and its 
   various options.

1. List the contents of your directory and make sure you see `homework1.tar`. Now, to make sure this
   tar file contains all of the work you just did, list all of its contents with the command:
   
   ```
   $ tar -tf homework1.tar
   ```

1. Now, to make this file smaller, we will compress it with `gzip`. Execute the command:

   ```
   $ gzip homework1.tar
   ```

   Read the manual page for `gzip` in section 1 of the manual to learn more about `gzip` and its
   various options.

1. List the contents of your directory and make sure you see `homework1.tar.gz` instead of 
   `homework1.tar`. Now, you have a compressed backup of your directory saved in the `.tar.gz file`.
   
1. Use the `submit` command to submit this exercise to `csci-1302`:
   
   ```
   $ submit homework1 csci-1302
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
