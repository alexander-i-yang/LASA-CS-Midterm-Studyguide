# C++
## Command line
### Why it’s around
* Invented b/c computers didn’t have a gui
* Still around because:
  * Easy to use
  * Flexibility with parameters
  * Scripts can be executed

### Commands (doesn’t include all params)
Name	| Description	| Example	| Parameters
------- | ------------- | ------------- | ----------
help | Displays list of available commands | `C:\>help` | none
help [cmd] | Displays info of command | `C:\>help cd` | [cmd]: command to display
cd [dir] | Navigates to the specified directory. Can go up the hierarchy and down | `C:\>cd users` | [dir]: directory to navigate to
cd.. | Navigates to above directory | `C:\Users\>cd..`
dir| Displays details about the current directory | `C:\>dir`
copy [file1] [file2] | Creates a copy of file1 with name file2 | `C:\>copy hello.cpp hello1.cpp` | [file1]: the original file
												   [file2]: the new file
copy con [newfile]
Copies what the user types into a new file. Ctrl+c, then enter to cancel, ctrl+z, then enter to create the file.
C:\>copy con hello.cpp
[newfile]: the file that stores the text in the command line
del [delfile]
Deletes a file. You must include the file type. (helo.cpp, not hello)
C:\>del hello.cpp
[delfile]: the file to delete
mkdir [dir]
Creates a folder/directory
C:\>mkdir hellos
[dir]: the directory to create
rmdir [dir]
Deletes a folder/directory
C:\>rmdir hellos
[dir]: the directory to delete
echo [stat]
Turns echo mode on/off
C:\>echo on
or
C:\>echo off
[stat]: can either be “on” (echo mode on) or “off” (echo mode off)
echo [msg]
Repeats a message
C:\>echo foo
[msg]: the message to repeat
[out] > [file]
Redirect output from [out] to [file]
C:\>echo foo > hello.txt
[out]: the text to put into [file]
[file]: the file name
[out] >> [file]
Append output from [out] to [file]
C:\>echo foo2 >> hello.txt
[out]: the text to append to [file]
[file]: the file name
[file] < [in]
Redirect input from [in] to [file]
???
[in]: the source of the input
[file]: the file name
[out] | [file]
Same as >
C:\>echo foo | hello.txt
Same as >

Batch files
Have extension .bat
Basically just macros with info in them
Create a “helloWorld.bat”:
Make it:
C:\>copy con helloWorld.bat
C:\>echo Hello World!
Ctrl+z, then enter
Run it:
C:\>helloWorld.bat
Pass parameters using “%”
Make it:
C:\>copy con helloWorld.bat
C:\>echo %1
Ctrl+z, then enter
Run it:
C:\>helloWorld.bat Helloworld! (cmd thinks spaces are flag separators)
Variables
General
Valid identifier:
No punctuation marks or spaces
Must begin with letter
Case sensitive
Size:
Depends on compiler (think back to Alex’s question fail)
Use “sizeof( [type] )” to get the size of [type]
ACRONYMS
CB S LIF DL (Cob is life dull)
CB: char/bool, S: short, LIF: long int/int/float, DL: double/long double
CB: 1 byte, S: 2 bytes, LIF: 4 bytes, DL: 8 bytes
Two ways of defining variables
int a = 0;
int a(0);
Const:
Makes a variable constant. Basically like #define except it’s only within the scope of the function
Implementation: const int yee = 10;
Can’t change value
Numerical
Unsigned vs. signed:
Unsigned saves an extra bit but can’t be negative
To declare:
unsigned int [name]
signed int [name]
Strings
Description
Powerpoint says we need to include <string> but you do not
Mutable
Implementation
string s = “”;
string s(“”);
Methods
Operator overloading actually works
string.length(): number of characters
string.size(): same as length()
Accessing individual characters
Only way is through string[]
Basically like an array
Find
string.find( [char_to_find], [index] )
Returns string::npos if it didn’t find anything
[index]: the index it starts looking at
string.rfind( [char], [last_index])
Reads from right to left
Returns string::npos if didn’t find
[last_index]: the index it starts looking at
string.substr( [pos], [len] )
[len]: is the length of the resulting string, not the index
string.erase( [pos], [len] )
[len]: the length of the string to remove
string.insert( [pos], [string2] )
Inserts [string2] into [string]
[pos]: starting pos
[string2]: the string to insert
IEEE 754
Types of representations:
Sign
1 bit
Stores sign of float (1 = negative, 0 = positive)
Exponent
8 bits on a 32 bit float
Stores exponent of float (with bias of 127)
Mantissa
23 bits on 32 bit float
Actual numerical value of float
How to convert:
Figure out the sign
If it’s negative, sign bit = 1
If it’s positive, sign bit = 0
Convert to binary
Convert integer component to binary
Convert decimal to binary
string binary(double d) {
 if(d == 0) return "";
 d *= 2;
 if(d >= 1) return "1" + binary(d-1);
 return "0" + binary(d);
}
Find the exponent
Convert the binary representation from 2) into scientific notation (one bit, then decimal point, then mantissa, then exponent)
Add 127 to the exponent
Convert exponent to binary
Save the mantissa
Remove the first bit from the mantissa
Put it all together
Preprocessor Directives
#define
Description:
Defines a global read-only constant
Should be all uppercase
Implementation:
#define E 2.718
No semicolons
#include
Includes a library (duh)

Control Flow
Do While loops
Description
Execute the loop body once
Checks state after looping once
Implementation
do { [loop] } while( [statement] );
Continue
Description
Skip over the rest of the loop body
Different from break because it doesn’t exit out of the loop
Implementation
while(true) {
	if(true) {
		continue;
	}
	cout << “Yee” << endl;
}
This will never print anything because the “continue” statement causes the loop to skip the print statement
Input
Console
Cin
Description:
Gets input from console
Separators are whitespace characters
Type istream
Getline
Description
Gets input from console
Separators are new lines
Function
Implementation
getline( [in], [var])
[in]: the source of input (usually cin)
[var]: the name of the variable where the input value is stored
getline( [in], [var], [terminate])
[terminate]: a character that specifies when getline() terminates
Misc
Stringstream
Description
Allows a string to be treated as a stream (like cin)
Helpful for converting a stream to different type
Use with getline()
Preferred method for all user input
Because it allows more control over user interaction
Implementation
stringstream( [string] ) >> [var]
[string]: the string to convert
[var]: the variable that will assume the value of [string]
Operators
Precedence

Operators in parentheses are examples.
Scope (::)
Postfix unary (var++)
Prefix unary (++var)
Pointer to member (->)
Multiplication (%)
Addition
Bitwise shift (>>)
Relational (<=)
Equality (==)
Bitwise and
Bitwise or
Bitwise xor
Logical and
Logical or
Assignment-level (*=, +=)
Ternary
Comma
Ternary (?:)
Description
one-line shorthand for if/else statement
Implementation
[condition] ? [if_true] : [if_false]
[condition]: the condition to test
[if_true]: runs if [condition] is true
[if_false]: runs if [condition] is false
Bitwise
1 = true, 0 = false
Works on numbers only

Operator
English plz
I said “English”
That’s not English
&
AND
Bitwise AND
Creates a new number with 1 and 1 only
|
OR
Bitwise inclusive OR
Creates a new number with 1 and 1, 1 and 0, or 0 and 1
^
XOR
Bitwise exclusive OR
Creates a new number with 1 and 0 or 0 and 1
~
NOT
Unary complement (bit inversion)
Switches the bits
<<
SHL
Shift bits left
[num1] >> [int] is like [num1] / (2 to the power of [int]). [int] can be ints only.
>>
SHR
Shift bits right
[num1] >> [int] is like [num1] * (2 to the power of [int]). [int] can be ints only.

Pointers (Samwell’s worst nightmare)
&
Description
“Address of” operator
Used to get the address of a variable
Implementation
&[var] means the address of [var]
You can really only assign pointers by pointing them to an address
*[]
