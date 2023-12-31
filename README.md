# Lollipop Language

Lollipop Language, also referred to as Lol-lang, is a modern computing language designed for implementing and using serverless functions on the web.

First conceptualized in 2016, it was inspired by Unix pipe-style commands and originally designed under the name Dexy-Lang to make programming accessible to anyone. However, its development was halted after the initial launch, and it is currently being planned for a rebirth under a new name.

The goal of this language is to allow anyone to easily program without understanding the underlying structure of web services, and to operate it in a Serverless environment without building a server. Moreover, while maintaining the basic structure of the language, it aims to enable natural language-based programming through the user's native language by integrating with AI, and to instantly check the results on the web.

To reliably operate user-implemented functions in Serverless, it implements a distributed processing system based on the Erlang VM, which is optimized for high availability. It also uses a Pluggable structure to allow anyone to develop and share underlying functions - a feature already implemented in Dexy-Lang.

## Getting Started

To get started with Lol-lang, you need to install the Lol-lang interpreter on your system. The interpreter handles the execution of your Lol-lang code.

### Basic Syntax

The basic unit of Lol-lang code is the pipeline. A pipeline is a series of operations that are applied to some input in order. Each operation in the pipeline is separated by the pipe character '|'.

Here's an example of a pipeline:

```lol
1..10 | for into: num | num | echo | end
```

or

```lol
1..10 | for | echo | end
```

Here's the breakdown:

- `1..10` generates a sequence of numbers from 1 to 10.
- `for into: num` is a loop construct that iterates over each number in the sequence, storing the current number into the num variable.
- `num` is an operation that simply returns the current number.
- `echo` prints the result of the preceding operation in the pipeline, which is the current number.
- `end` terminates the for loop.

So, this code will print the numbers 1, 2, 3, ..., 10, each on a new line.

### Function Definition and Calling

Functions can be defined using the 'fn' keyword. A function is a code block that takes input and generates output. For example, the following code defines a function that doubles a given number and then calls it:

```lol
fn double x: 0 | x * 2 | end
1..5 | for into: num | double num | echo | end
```

or

```lol
fn double | _v * 2 | end
1..5 | for | double | echo | end
```

Here's the breakdown:

- `fn double x: 0 | x * 2 | end` defines a function named double that takes a parameter x with a default value of 0. This function multiplies x by 2 and returns the result.
- `1..5` generates a sequence of numbers from 1 to 5.
- `for into: num` is the loop construct that iterates over each number in the sequence, storing the current number into the num variable.
- `double num` calls the double function with the current number as the argument, doubling the number.
- `echo` prints the result of the preceding operation in the pipeline, which is the doubled number.
- `end` terminates the for loop.
  
So, this code will print the numbers 2, 4, 6, 8, and 10, which are the double of each number from 1 to 5.

### Loops and Control Structures

The 'for' construct is the basic structure for loops. The 'for' loop executes a block of code for each item in the pipeline. For example, the code above repeats the action of assigning a value to the 'num' variable and printing it for each number from 1 to 10.

The 'if' construct is used for conditional execution. 'if' only executes its code block when the given condition is true. For example, the following code prints only the odd numbers from 1 to 10:

```lol
1..10 | for into: num | if num % 2 | num | echo | end | end
```

or

```lol
1..10 | for | if _v % 2 | echo | end | end
```

Here's the breakdown:

- `1..10` generates a sequence of numbers from 1 to 10.
- `for into: num` is the loop construct that iterates over each number in the sequence, storing the current number into the `num` variable.
- `if num % 2` checks if the current number is odd. The `%` operator calculates the remainder of the division of `num` by 2. If `num` is odd, `num % 2` will be 1, which is truthy in a boolean context, so the code inside the `if` block will execute.
- `num` is an operation that simply returns the current number.
- `echo` prints the result of the preceding operation in the pipeline, which is the current number if it's odd.
- The first `end` terminates the `if` statement.
- The second `end` terminates the `for` loop.

So, this code will print the odd numbers 1, 3, 5, 7, 9, each on a new line.

### Using the `_v` Variable in Lol-lang

In Lol-lang, the `_v` variable is a special variable that automatically captures the value of each item in the pipeline. This makes it especially useful in loops and other constructs where you need to perform operations on each item in a sequence.

Here's how you can use the `_v` variable:

```
1..5 | for | _v * 2 | echo | end
```

Breaking down this code:

- `1..5` is the input, generating a sequence of numbers from 1 to 5.
- `for` is the loop construct that iterates over each number in the input sequence.
- `_v * 2` doubles the value of each number in the sequence. `_v` automatically captures the value of each item from the `for` loop.
- `echo` prints the result of the preceding operations in the pipeline.
- `end` terminates the `for` loop.

So, this code will print the numbers 2, 4, 6, 8, and 10, which are the double of each number from 1 to 5.

The `_v` variable can be used in any pipeline where you need to work with the current item. It's a powerful tool that can simplify your Lol-lang code and make it easier to read and understand.
