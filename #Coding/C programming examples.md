#  C programming examples 

_Captured from [ProgrammingSimplified](http://www.programmingsimplified.com/c-program-examples)_

C programming examples: These programs illustrate various programming elements, concepts such as using operators, loops, functions, single and double dimensional arrays, performing operations on strings, files, pointers etc. Browse the code from simple c program to complicated ones you are looking for, every one of them is provided with output. C program download with executable files, so that you save on your computer and run programs without compiling the source code. All programs are made using _c programming language_ and Codeblocks, most of these will work under [Dev C++ compiler](http://sourceforge.net/projects/orwelldevcpp/files/latest/download) also. Download software you need to develop codes. The first program prints "Hello World" on screen.

## C programming codes

  * [Hello world](http://www.programmingsimplified.com/c-hello-world-program)
  * [Print Integer](/c/program/print-integer)
  * [Addition](/c-program-add-two-numbers)
  * [Odd or Even](/c/source-code/c-program-check-odd-even)
  * [Add, subtract, multiply and divide](/c/program/addition-subtraction-multiplication-and-division)
  * [Check vowel](/c/source-code/c-program-check-vowel)
  * [Leap year](/c/source-code/c-program-check-leap-year)
  * [Add digits](/c/program/c-program-add-number-digits)
  * [Factorial](/c-program-find-factorial)
  * [HCF and LCM](/c/source-code/c-program-find-hcf-and-lcm)
  * [Decimal to binary conversion](/c/source-code/c-program-convert-decimal-to-binary)
  * [ncR and nPr](/c/source-code/c-program-find-ncr-and-npr)
  * [Add n numbers](/c-program-add-n-numbers)
  * [Swapping](/c-program-swap-two-numbers)
  * [Reverse number](/c/source-code/c-program-reverse-number)
  * [Palindrome number](/c/source-code/c-program-palindrome-number)
  * [Print Pattern](/c-program-print-stars-pyramid)
  * [Diamond](/c/source-code/c-program-print-diamond-pattern)
  * [Prime numbers](/c/source-code/c-program-for-prime-number)
  * [Find armstrong number](/c-program-find-armstrong-number)
  * [Generate armstrong number](/c-program-generate-armstrong-number)
  * [Fibonacci series ](/c-program-generate-fibonacci-series)
  * [Print floyd's triangle](/c-program-print-floyd-triangle)
  * [Print pascal triangle](/c-program-print-pascal-triangle)
  * [Addition using pointers](/c-program-add-two-numbers-using-pointers)
  * [Maximum element in array](/c/source-code/c-program-find-maximum-element-in-array)
  * [Minimum element in array](/c/source-code/c-program-find-minimum-element-in-array)
  * [Linear search](/c/source-code/c-program-linear-search)
  * [Binary search](/c/source-code/c-program-binary-search)
  * [Reverse array](/c-program-reverse-array)
  * [Insert element in array](/c/source-code/c-program-insert-element-in-array)
  * [Delete element from array](/c/source-code/c-program-delete-element-from-array)
  * [Merge arrays](/c/source-code/c-program-merge-two-arrays)
  * [Bubble sort](/c/source-code/c-program-bubble-sort)
  * [Insertion sort](/c/source-code/c-program-insertion-sort)
  * [Selection sort](/c/source-code/c-program-selection-sort)
  * [Add matrices](/c-program-add-matrices)
  * [Subtract matrices](/c/source-code/c-program-subtract-matrices)
  * [Transpose matrix](/c-program-transpose-matrix)
  * [Multiply two matrices](/c-program-multiply-matrices)
  * [Print string](/c/program/print-string)
  * [String length](/c-program-find-string-length)
  * [Compare strings](/c-program-compare-two-strings)
  * [Copy string](/c/source-code/c-program-copy-strings)
  * [Concatenate strings](/c-program-concatenate-strings)
  * [Reverse string](/c-program-reverse-string)
  * [Find palindrome](/c-program-find-palindrome)
  * [String to integer](/c/source-code/c-program-convert-string-to-integer-without-using-atoi-function)
  * [Delete vowels](/c/source-code/c-program-remove-vowels-from-string)
  * [C substring](/c/source-code/c-substring)
  * [Check subsequence](c/source-code/c-program-check-subsequence)
  * [Sort a string](/c/source-code/c-program-sort-string)
  * [Remove spaces](/c/source-code/c-program-remove-spaces-string)
  * [Change case](/c/program/c-program-change-case)
  * [Swap strings](/c-program-swap-two-strings)
  * [Character's frequency](/c-program-find-characters-frequency)
  * [Anagrams](/c/source-code/c-anagram-program)
  * [Read file](/c-program-read-file)
  * [Copy files](/c-program-copy-file)
  * [Merge two files](/c-program-merge-two-files)
  * [List files in a directory](/c-program-list-files-in-directory)
  * [Delete file](/c-program-delete-file)
  * [Random numbers](/c-program-generate-random-numbers)
  * [Add complex numbers](/c-program-add-two-complex-numbers)
  * [Print date](/c/program/print-date)
  * [Get IP address](/c-program-get-ip-address)
  * [Shutdown computer](/c-program-shutdown-computer)

## C program examples

Example 1 - C hello world program  
/* A very simple c program printing a string on screen*/

    
    
    #include <stdio.h>
     
    main()
    {
        printf("Hello World\n");
        return 0;
    }

Output of above program:  
"Hello World"

Example 2 - c program to take input from user using scanf

    
    
    #include <stdio.h>
     
    main()
    {
       int number;
     
       printf("Enter an integer\n");
       scanf("%d",&number);
     
       printf("Integer entered by you is %d\n", number);
     
       return 0;
    }

Output:  
Enter a number  
5  
Number entered by you is 5

Example 3 - using if else control instructions

    
    
    #include <stdio.h>
     
    main()
    {
       int x = 1;
     
       if ( x == 1 )
          printf("x is equal to one.\n");
       else
          printf("For comparison use == as = is the assignment operator.\n");
     
       return 0;
    }

Output:  
x is equal to one.

Example 4 - loop example

    
    
    #include <stdio.h>
     
    main()
    {
       int value = 1;
     
       while(value<=3)
       {
          printf("Value is %d\n", value);
          value++;
       }
     
       return 0;
    }

Output:  
Value is 1  
Value is 2  
Value is 3

Example 5 - c program for prime number

    
    
    #include <stdio.h>
     
    main()
    {
       int n, c;
     
       printf("Enter a number\n");
       scanf("%d", &n);
     
       if ( n == 2 )
          printf("Prime number.\n");
       else
       {
           for ( c = 2 ; c <= n - 1 ; c++ )
           {
               if ( n % c == 0 )
                  break;
           }
           if ( c != n )
              printf("Not prime.\n");
           else
              printf("Prime number.\n");
       }
       return 0;
    }

Example 6 - command line arguments

    
    
    #include <stdio.h>
     
    main(int argc, char *argv[])
    {
       int c;
     
       printf("Number of command line arguments passed: %d\n", argc);
     
       for ( c = 0 ; c < argc ; c++)
          printf("%d. Command line argument passed is %s\n", c+1, argv[c]);
     
       return 0;
    }

Above c program prints the number and all arguments which are passed to it.

Example 7 - Array program

    
    
    #include <stdio.h>
     
    main() 
    {
        int array[100], n, c;
     
        printf("Enter the number of elements in array\n");
        scanf("%d", &n);
     
        printf("Enter %d elements\n", n);
     
        for ( c = 0 ; c < n ; c++ ) 
            scanf("%d", &array[c]);
     
        printf("Array elements entered by you are:\n");
     
        for ( c = 0 ; c < n ; c++ ) 
            printf("array[%d] = %d\n", c, array[c]);
     
        return 0;
    }

Example 8 - function program

    
    
    #include <stdio.h>
     
    void my_function();
     
    main()
    {
       printf("Main function.\n");
     
       my_function();
     
       printf("Back in function main.\n");
     
       return 0;
    }
     
    void my_function()
    {
       printf("Welcome to my function. Feel at home.\n");
    }

Example 9 - Using comments in a program

    
    
    #include <stdio.h>
     
    main()
    {
       // Single line comment in c source code
     
       printf("Writing comments is very useful.\n");
     
       /*
        * Multi line comment syntax
        * Comments help us to understand code later easily.
        * Will you write comments while developing programs ?
        */
     
       printf("Good luck c programmer.\n"); 
     
       return 0;
    }

Example 10 - using structures in c programming

    
    
    #include <stdio.h>
     
    struct programming
    {
        float constant;
        char *pointer;
    };
     
    main()
    {
       struct programming variable;
       char string[] = "Programming in Software Development.";   
     
       variable.constant = 1.23;
       variable.pointer = string;
     
       printf("%f\n", variable.constant);
       printf("%s\n", variable.pointer);
     
       return 0;
    }

Example 11 - c program for Fibonacci series

    
    
    #include <stdio.h>
     
    main()
    {
       int n, first = 0, second = 1, next, c;
     
       printf("Enter the number of terms\n");
       scanf("%d",&n);
     
       printf("First %d terms of Fibonacci series are :-\n",n);
     
       for ( c = 0 ; c < n ; c++ )
       {
          if ( c <= 1 )
             next = c;
          else
          {
             next = first + second;
             first = second;
             second = next;
          }
          printf("%d\n",next);
       }
     
       return 0;
    }

Example 12 - c graphics programming

    
    
    #include <graphics.h>
    #include <conio.h>
     
    main()
    {
        int gd = DETECT, gm;
     
        initgraph(&gd, &gm,"C:\\TC\\BGI");
     
        outtextxy(10,20, "Graphics source code example.");
     
        circle(200, 200, 50);
     
        setcolor(BLUE);
     
        line(350, 250, 450, 50);
     
        getch();
        closegraph( );
        return 0;
    }

## For GCC users

If you are using GCC on Linux operating system then you need to modify programs. For example consider the following program which prints first ten natural numbers

    
    
    #include <stdio.h>
    #include <conio.h>
     
    int main()
    {
        int c;
     
        for ( c = 1 ; c <= 10 ; c++ )
            printf("%d\n", c);
     
        getch();
        return 0;
    }

Above source code includes a header file `<conio.h>` and uses function getch, but this file is Borland specific so it works in turbo c compiler but not in GCC. So the code for GCC should be like

    
    
    #include <stdio.h>
     
    int main()
    {
        int c;
     
        /* for loop */
     
        for ( c = 1 ; c <= 10 ; c++ )
            printf("%d\n", c);
     
        return 0;
    }

If using GCC then save the code in a file say “numbers.c”, to compile the program open the terminal and enter command “gcc numbers.c”, this will compile the program and to execute the program enter command “./a.out”, do not use quotes while executing commands.

## C programming tutorial

C program consists of functions and declarations or instructions given to the computer to perform a particular task. The process of writing a program involves designing the algorithm, a flowchart may also be drawn, and then writing the source code, after developing the program you need to test it and debug it if it does not meet the requirement. To make a program you need a text editor and a compiler. You can use any text editor of your choice and a compiler. C compiler converts source code into machine code that consists of zero and one only and directly executed on machine. An IDE or Integrated Development Environment provides a text editor, compiler, debugger etc. for developing programs or projects. [Download Codeblocks IDE](http://www.codeblocks.org/downloads/binaries) it provides an ideal environment for development. It can import Microsoft Visual C++ projects, extendable as it uses plug-ins, open source and cross platform. 

A c program must have at least one function which is main, function consists of declaration and statements, a statement is an expression followed by a semicolon, for example a + b, printf("c program examples") are expressions and a + b; and printf("C is an easy to learn computer programming language."); are statements. To use a variable we must indicate its type whether it is an integer, float, character. C language has many built in data types and we can make our own using structures and unions. Every data type has its own size that may depend on machine for example an integer may be of 2 or 4 Bytes. Data is stored in binary form i.e. group of bits where each bit may be '0' or '1'. Keywords such as switch, case, default, register etc. are special words with predefined meaning and can't be used for other purposes. Memory can be allocated during compile time or at run time using malloc or calloc. C language has many features such as recursion, preprocessor, conditional compilation, portability, pointers, multi threading by using external libraries, dynamic memory allocation due to which it is used for making portable software programs and applications. Networking API's are available using which computer users can communicate and interact with each other, share files etc. C standard library offers functions for mathematical operations, character strings and input/output and time. The process of making programs which is known as coding requires knowledge of programming language and logic to achieve the desired output. So you should learn c programming basics and start making programs. Learning data structures such as stacks, queues, linked lists etc. using c programming provides you a greater understanding as you learn everything in detail. General belief is to go for other high level languages but it's a good idea to learn c before learning C++ or Java. C++ programming language is object oriented and it contains all the features of c language so learning c first will help you to easily learn C++ and then you can go for Java programming.

