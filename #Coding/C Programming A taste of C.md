# C Programming/A taste of C

_Captured: 2015-07-18 at 11:19 from [en.m.wikibooks.org](https://en.m.wikibooks.org/wiki/C_Programming/A_taste_of_C)_

As with nearly every other programming language learning book, we use the _[Hello world](//en.wikipedia.org/wiki/Hello_world_program)_ program to introduce you to C.
    
    
    #include <stdio.h>
    
    int main(void)
    {
       puts("Hello, world!");
       return 0;
    }
    

This program prints "Hello, world!" and then exits.

And if you want to hold the output and it does not exit, you may use the `getchar();` as following:
    
    
    #include <stdio.h>
    
    int main(void)
    {
       puts("Hello, world!");
       getchar();
       return 0;
    }
    

Enter this code into your text editor or IDE, and save it as "hello.c".

Then, presuming you are using GCC, type `gcc -o hello hello.c`. This tells gcc to compile your hello.c program into a form the machine can execute. The '-o hello' tells it to call the compiled program 'hello'.

If you have entered this correctly, you should now see a file called hello. This file is the binary version of your program, and when run should display "Hello, world!"

Here is an example of how compiling and running looks when using a terminal on a unix system. `ls` is a common unix command that will list the files in the current directory, which in this case is the directory `progs` inside the home directory (represented with the special tilde, ~, symbol). After running the `gcc` command, `ls` will list a new file, `hello` in green. Green is the standard color coding of `ls` for executable files.
    
    
    ~/progs$ ls
    hello.c
    ~/progs$ gcc -o hello hello.c
    ~/progs$ ls
    hello  hello.c
    ~/progs$ ./hello
    Hello, world!
    ~/progs$
    

`#include <stdio.h>` tells the C compiler to find the standard header called _<[stdio.h>](//en.wikipedia.org/wiki/stdio.h)_ and add it to this program. In C, you often have to pull in extra optional components when you need them. _<stdio.h>_ contains descriptions of standard input/output functions which you can use to send messages to a user, or to read input from a user.

`int main(void)` is something you'll find in every C program. Every program has a _main_ function. Generally, the main function is where a program begins. However, one C program can be scattered across multiple files, so you won't always find a main function in every file. The _int_ at the beginning means that main will return an integer to the operating system when it is finished.

`puts("Hello, world!");` is the statement that actually puts the message to the screen. _puts_ is a string printing function that is declared in the file _stdio.h_ (which is why you had to _#include_ that at the start of the program) `puts` automatically prints a newline at the end of the string.

`return 0;` will return zero (which is the [integer](//en.wikipedia.org/wiki/en:Integer_\(computer_science\)) referred to on line 3) to the operating system. When a program runs successfully its return value is zero (GCC4 complains if it doesn't when compiling). A non-zero value is returned to indicate a warning or error.

The empty line is there because it is (at least on UNIX) considered good practice to end a file with a new line. In gcc using the `-Wall -pedantic -ansi` options, if the file does not end with a new line this message is displayed: "warning: no newline at end of file". (The newline isn't shown on the example because MediaWiki automatically removes it)
