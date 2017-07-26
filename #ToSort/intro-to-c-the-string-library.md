# Intro to C – the string library

_Captured: 2017-05-20 at 10:31 from [www.raspberrypi.org](https://www.raspberrypi.org/magpi/c-string-library/)_

![](https://www.raspberrypi.org/magpi/wp-content/uploads/2017/03/string.png)

In chapter seven, we saw how to join two strings together using pointers. We're now going to do the same thing using the string handling library, which saves a lot of space.

_The full article and many more that will introduce you to C, check out [Learn to code with C](https://www.raspberrypi.org/magpi/issues/magpi/essentials-c-v1) written by Simon Long._

![Learn to Code with C](https://www.raspberrypi.org/magpi/wp-content/uploads/2016/10/eBook_8-Code-C.png)

> _Learn to code with C in our Essentials book!_

1234567891011 
#include <stdio.h>#include <string.h>void main (void){char str1[10] = "first";char str2[10] = "second";char str3[20];strcpy (str3, str1);strcat (str3, str2);printf ("%s + %s = %s\n", str1, str2, str3);}?

Note the #include <string.h> at the start, which tells the compiler that we want to use functions from the string library.

This shows two string functions. strcpy ('string copy') copies the string at the second argument to the start of string at the first argument. strcat ('string concatenate') does the same thing, but instead it finds the terminating zero of the first argument and starts copying to its location, thereby joining the two strings together.

### Comparing strings

We use the == operator to compare numeric values, but this doesn't work with strings. The name of a string is actually a pointer to a location in memory containing the string, so using == to compare two strings will only tell you if they are at the same place in memory.

You can use == to compare two char variables, and a string is an array of chars, so it is possible to write a simple piece of code that compares each character in a string in turn:

123456789101112131415161718192021222324 
#include <stdio.h>void main (void){char str1[10] = "first";char str2[10] = "fire";char *ptr1 = str1, *ptr2 = str2;while (*ptr1 != 0 && *ptr2 != 0){if (*ptr1 != *ptr2){break;}ptr1++;ptr2++;}if (*ptr1 == 0 && *ptr2 == 0){printf ("The two strings are identical.\n");}else{printf ("The two strings are different.\n");}}

The string library makes this much easier with strcmp (for 'string compare'):

123456789101112131415 
#include <stdio.h>#include <string.h>void main (void){char str1[10] = "first";char str2[10] = "fire";if (strcmp (str1, str2) == 0){printf ("The two strings are identical.\n");}else{printf ("The two strings are different.\n");}}

strcmp takes two strings as arguments, and returns a 0 if they are the same; it returns a non-zero value if not.

To compare the first few characters of a string, use the function strncmp (for 'string numbered compare'). This works in the same way as strcmp, but it takes a third argument, an integer giving the number of characters to compare. So strncmp ("first", "fire", 4) would return a non-zero value, while strncmp ("first", "fire", 3) would return a 0.

### Reading values from a string

The function sscanf ('string scan formatted') can be used to read variables from a string:

12345678 
#include <stdio.h>void main (void){int val;char string[10] = "250";sscanf (string, "%d", &val);printf ("The value in the string is %d\n", val);}

sscanf uses the same format specifiers as printf, but all its arguments must be pointers to variables rather than variables themselves: as always, a function can never change the values of variables provided as arguments, but it can write to their destinations if they are pointers.

sscanf returns the number of values successfully read. So if a format specifier of %d is provided but the string supplied doesn't start with a decimal number, sscanf will write nothing to the supplied pointer and will return 0; if the string supplied does start with a decimal number, sscanf will return 1.  
The format string supplied to sscanf can have multiple format specifiers and even other text:

123456789101112131415 
#include <stdio.h>void main (void){int val;char result[10];char string[25] = "The first number is 1";if (sscanf (string, "The %s number is %d", result, &val) == 2){printf ("String : %s Value : %d\n", result, val);}else{printf ("I couldn't find two values in that string.\n");}}

Note that, slightly inconsistently, the %s format specifier denotes a pointer to a string in both printf and sscanf, while the %d specifier denotes a variable in printf but a pointer in sscanf.

### How long is a (piece of) string?

One other string handling function is strlen (for 'string length') - this tells you how many characters are in a string, including the terminating zero character.

All the string operations above are possible by manipulating pointers, but the string library makes life much easier!
