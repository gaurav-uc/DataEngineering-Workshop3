# Python Debugging and Profiling 

## Python Debugger

### Introduction to Debugging in Python
As Programmers we are definitely familier with the term "bug". A bug in the code is when our code is not working as expected.
Sometimes the bug will be due to a logical error and rarely it will be due to Syntax errors.

Note that the bugs cause due to Syntax errors are easier to fix compared to logical errors.
#####
A popular saying by Anonymous:
#### Where there is code there is a bug and where there is a bug, there may or may not be a fix!

When a code breaks (has a bug) due to Syntax error, it is easier to find out the reason.
For example, consider the following:
```commandline
a = 10
if a > 5:
	print("Greater than 5")
else
	print("Greater than 5")

```
Here there is a missing colon after `else` and hence can expect an error while running this code.
```commandline
  File "breakpoint_demo_2.py", line 4
    else
       ^
SyntaxError: invalid syntax
```

<b>The process of finding out the bugs in the code and solving them is called as "Debugging".</b>

<b>Logical Errors</b> are harder to solve because most of the time it won't be straight forward and easily visible unlike <b>Syntax</b> errors. Hence to debug complex logical or semantic errors, we need to use something called as a "Debugger".

A Debugger is a software that allows the Programmer to find out and fix bug in their code.

In Python the in-built or default Debugger is called PDB or Python Debugger.

### Debugging the code in Python

Copy the following program to a text file and save it as `breakpoint_demo.py`:
```
print("This is line number 1")

a = 1
b = 2

sum = a + b

print(f"The sum is {sum}")

for i in range(5):
	sum += 1

print(f"The sum at the end is {sum}")

```

Now you can debug this file in one of two ways:
1. From the command line.
2. By importing the "pdb" module in the code.

#### Command Line 
Run the following command in the command line and you will see the Python Debugger in action:

```python3 -m pdb breakpoint_demo.py```

We will explore this in further depth later, for now you can press `q` to quit the debugger.

#### Importing the module
Now instead of using `-m pdb` in the Command Line, let us import the pdb module inside the code.

Open your code and add the below two lines in the beginning:
```commandline
import pdb
pdb.set_trace()
```

Now your code should look something like this:
```
import pdb
pdb.set_trace()

print("This is line number 1")

a = 1
b = 2

sum = a + b

print(f"The sum is {sum}")

for i in range(5):
	sum += 1

print(f"The sum at the end is {sum}")

```
Now you can run this code in your terminal as follows:
```commandline
python3 breakpoint_demo.py
```
You can observe that the output should be similar to that of running with `-m pdb` in the command line.
For now you can press `q` to quit the debugger.

In Python versions 2.7 and below 3.7 this was the way Python code used to be debugged.
But for Python versions 3.7 and higher, a new method `breakpoint()` was introduced.

In your previous code replace both these lines
```commandline
import pdb
pdb.set_trace()
```
with
```commandline
breakpoint()
```
And run the file:
```commandline
python3 breakpoint_demo.py
```
The experience should be similar as while you were using `pdb` and `breakpoint`.

### Various Commands available in Python Debugger 

1. b(reak): Breakpoint Command
    * b(reak) without any arguments lists us all the breakpoint set.
    * b(reak)<line number>: Sets a breakpoint in the current file for given line number.
    * b(reak) <path to directory/filename>:<line number> : if you want to set a breakpoint in another file.
2. tbreak: Temporary breakpoint, which is removed automatically when it is first hit.
    * Same argument as break.
3. p: Print the value of an expression.
    * Syntax: p variable_name_to_print
4. pp: Pretty-print the value of an expression.
   * Syntax: Similar to p
5. Stepping Through Code: 
   * n(ext): We navigate through each line of the code and continue execution until the next line and stay within the current function.
   * s (tep): Is used when we want execute the current line and stop in a foreign function if one is called.
6. Listing Source Code:
   * l(ist): List source code for the current file.
   * Syntax: l <line_number>: Display the current line of execution.
   * Syntax: l <line_number_start, line_number_end>: Display the set of code from where the start and end line number is mentioned.
   * ll(longlist): List source code for the current function or frame. It is available in Python 3.
7. Managing breakpoints:
   * disable: We can disable a particular breakpoint.
     * Syntax: disable <break_point_number>
   * enable: We can enable a particular breakpoint.
     * Syntax: enable <break_point_number>
   * cl(ear): Clears the breakpoint set.
     * cl(ear) all: Removes all the breakpoints.
     * cl(ear) <break_point_number>: Removes the specified breakpoint.
8. Continuing Execution: 
   * c(ontinue): We use continue to execute the rest of the code.
9. Stack Trace your python code: Syntax: w(here)
   * u(p):  Move to the frame above.
     * syntax: u(p) : Moves 1 frame up. Basically the caller of the current function.
     * syntax: u(p) <count>: Moves specific number of frames up.
   * d(own): Move to the frame below.
     * syntax: d(own) : Moves 1 frame down.
     * syntax: d(own) <count>: Moves specific number of frames down.
   * a(lias) or args: prints the argument list of the current function.  
   * unalias: Deletes the specified alias.
   * j(ump): Jumps to the code specified inside a current frame.
10. Exit pdb:
   * You can either type q(uit) or exit.

### Python Debugger Commands Demo

Add a `breakpoint()` to the first line of youe previous code.

As we had seen in the previous section, there are various commands that can be used to debug the code. You are already familier with `q` which is used to quit the debugger.

Now let us look at `n` and `b`. Once you run the code, keep pressing `n` and observe that you code is being executed one line at a time. Also try printing the values of variables like `sum` and print the value of `sum after every iteration inside the for-loop.

To learn about `b`, rerun the program and type `b 8` and press `c`. Now your execution should stop at 8th line. Note that `c` continued the execution until the line number where you had applied the breakpoint.

### Python Debugger Official Documentation
For the official Documentation of PDB, please refer: https://docs.python.org/3/library/pdb.html
Also try experimenting with different commands given in the section "Various Commands available in Python Debugger" for your program.








