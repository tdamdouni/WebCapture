# Automate the Boring Stuff with Python

_Captured: 2015-06-15 at 22:53 from [automatetheboringstuff.com](https://automatetheboringstuff.com/chapter0/)_

"You've just done in two hours what it takes the three of us two days to do." My college roommate was working at a retail electronics store in the early 2000s. Occasionally, the store would receive a spreadsheet of thousands of product prices from its competitor. A team of three employees would print the spreadsheet onto a thick stack of paper and split it among themselves. For each product price, they would look up their store's price and note all the products that their competitors sold for less. It usually took a couple of days.

"You know, I could write a program to do that if you have the original file for the printouts," my roommate told them, when he saw them sitting on the floor with papers scattered and stacked around them.

After a couple of hours, he had a short program that read a competitor's price from a file, found the product in the store's database, and noted whether the competitor was cheaper. He was still new to programming, and he spent most of his time looking up documentation in a programming book. The actual program took only a few seconds to run. My roommate and his co-workers took an extra-long lunch that day.

This is the power of computer programming. A computer is like a Swiss Army knife that you can configure for countless tasks. Many people spend hours clicking and typing to perform repetitive tasks, unaware that the machine they're using could do their job in seconds if they gave it the right instructions.

Software is at the core of so many of the tools we use today: Nearly everyone uses social networks to communicate, many people have Internet-connected computers in their phones, and most office jobs involve interacting with a computer to get work done. As a result, the demand for people who can code has skyrocketed. Countless books, interactive web tutorials, and developer boot camps promise to turn ambitious beginners into software engineers with six-figure salaries.

This book is not for those people. It's for everyone else.

On its own, this book won't turn you into a professional software developer any more than a few guitar lessons will turn you into a rock star. But if you're an office worker, administrator, academic, or anyone else who uses a computer for work or fun, you will learn the basics of programming so that you can automate simple tasks such as the following:

  * Moving and renaming thousands of files and sorting them into folders

  * Filling out online forms, no typing required

  * Downloading files or copy text from a website whenever it updates

  * Having your computer text you custom notifications

  * Checking your email and sending out prewritten responses

These tasks are simple but time-consuming for humans, and they're often so trivial or specific that there's no ready-made software to perform them. Armed with a little bit of programming knowledge, you can have your computer do these tasks for you.

This book is not designed as a reference manual; it's a guide for beginners. The coding style sometimes goes against best practices (for example, some programs use global variables), but that's a trade-off to make the code simpler to learn. This book is made for people to write throwaway code, so there's not much time spent on style and elegance. Sophisticated programming concepts--like object-oriented programming, list comprehensions, and generators--aren't covered because of the complexity they add. Veteran programmers may point out ways the code in this book could be changed to improve efficiency, but this book is mostly concerned with getting programs to work with the least amount of effort.

Television shows and films often show programmers furiously typing cryptic streams of 1s and 0s on glowing screens, but modern programming isn't that mysterious. _Programming_ is simply the act of entering instructions for the computer to perform. These instructions might crunch some numbers, modify text, look up information in files, or communicate with other computers over the Internet.

All programs use basic instructions as building blocks. Here are a few of the most common ones, in English:

  * **"Do this; then do that."**

  * **"If this condition is true, perform this action; otherwise, do that action."**

  * **"Do this action that number of times."**

  * **"Keep doing that until this condition is true."**

You can combine these building blocks to implement more intricate decisions, too. For example, here are the programming instructions, called the _source code_, for a simple program written in the Python programming language. Starting at the top, the Python software runs each line of code (some lines are run only _if_ a certain condition is true or _else_ Python runs some other line) until it reaches the bottom.
    
    
    ➊ passwordFile = open('SecretPasswordFile.txt')
    ➋ secretPassword = passwordFile.read()
    ➌ print('Enter your password.')
      typedPassword = input()
    ➍ if typedPassword == secretPassword:
    ➎    print('Access granted')
    ➏    if typedPassword == '12345':
    ➐       print('That password is one that an idiot puts on their luggage.')
      else:
    ➑    print('Access denied')

You might not know anything about programming, but you could probably make a reasonable guess at what the previous code does just by reading it. First, the file _SecretPasswordFile.txt_ is opened ➊, and the secret password in it is read ➋. Then, the user is prompted to input a password (from the keyboard) ➌. These two passwords are compared ➍, and if they're the same, the program prints _Access granted_ to the screen ➎. Next, the program checks to see whether the password is _12345_ ➏ and hints that this choice might not be the best for a password ➐. If the passwords are not the same, the program prints _Access denied_ to the screen ➑.

_Python_ refers to the Python programming language (with syntax rules for writing what is considered valid Python code) and the Python interpreter software that reads source code (written in the Python language) and performs its instructions. The Python interpreter is free to download from _<http://python.org/>_, and there are versions for Linux, OS X, and Windows.

The name Python comes from the surreal British comedy group Monty Python, not from the snake. Python programmers are affectionately called Pythonistas, and both Monty Python and serpentine references usually pepper Python tutorials and documentation.

The most common anxiety I hear about learning to program is that people think it requires a lot of math. Actually, most programming doesn't require math beyond basic arithmetic. In fact, being good at programming isn't that different from being good at solving Sudoku puzzles.

To solve a Sudoku puzzle, the numbers 1 through 9 must be filled in for each row, each column, and each 3×3 interior square of the full 9×9 board. You find a solution by applying deduction and logic from the starting numbers. For example, since 5 appears in the top left of the Sudoku puzzle shown in [Figure 1](https://automatetheboringstuff.com/chapter0/), it cannot appear elsewhere in the top row, in the leftmost column, or in the top-left 3×3 square. Solving one row, column, or square at a time will provide more number clues for the rest of the puzzle.

![A new Sudoku puzzle \(left\) and its solution \(right\). Despite using numbers, Sudoku doesn’t involve much math. \(Images © Wikimedia Commons\)](https://automatetheboringstuff.com/images/000037.jpg)

> _Figure 1. A new Sudoku puzzle (left) and its solution (right). Despite using numbers, Sudoku doesn't involve much math. (Images (C) Wikimedia Commons)_

Just because Sudoku involves numbers doesn't mean you have to be good at math to figure out the solution. The same is true of programming. Like solving a Sudoku puzzle, writing programs involves breaking down a problem into individual, detailed steps. Similarly, when _debugging_ programs (that is, finding and fixing errors), you'll patiently observe what the program is doing and find the cause of the bugs. And like all skills, the more you program, the better you'll become.

Programming is a creative task, somewhat like constructing a castle out of LEGO bricks. You start with a basic idea of what you want your castle to look like and inventory your available blocks. Then you start building. Once you've finished building your program, you can pretty up your code just like you would your castle.

The difference between programming and other creative activities is that when programming, you have all the raw materials you need in your computer; you don't need to buy any additional canvas, paint, film, yarn, LEGO bricks, or electronic components. When your program is written, it can easily be shared online with the entire world. And though you'll make mistakes when programming, the activity is still a lot of fun.

![The Google results for an error message can be very helpful.](https://automatetheboringstuff.com/images/000042.jpg)

> _Figure 2. The Google results for an error message can be very helpful._
