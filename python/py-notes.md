Key takeaways
1. The print() function is a built-in function. It prints/outputs a specified message to the screen/consol window.
2. Built-in functions, contrary to user-defined functions, are always available and don't have to be imported. Python 3.8 comes with 69 built-in functions. You can find their full list provided in alphabetical order in the Python Standard Library.
3. To call a function (this process is known as function invocation or function call), you need to use the function name followed by parentheses. You can pass arguments into a function by placing them inside the parentheses. You must separate arguments with a comma, e.g., print("Hello,", "world!"). An "empty" print() function outputs an empty line to the screen.
4. Python strings are delimited with quotes, e.g., "I am a string" (double quotes), or 'I am a string, too' (single quotes).
5. Computer programs are collections of instructions. An instruction is a command to perform a specific task when executed, e.g., to print a certain message to the screen.
6. In Python strings the backslash (\) is a special character which announces that the next character has a different meaning, e.g., \n (the newline character) starts a new output line.
7. Positional arguments are the ones whose meaning is dictated by their position, e.g., the second argument is outputted after the first, the third is outputted after the second, etc.
8. Keyword arguments are the ones whose meaning is not dictated by their location, but by a special word (keyword) used to identify them.
9. The end and sep parameters can be used for formatting the output of the print() function. The sep parameter specifies the separator between the outputted arguments (e.g., print("H", "E", "L", "L", "O", sep="-"), whereas the end parameter specifies what to print at the end of the print statement.


4 is an integer number, whereas 4.0 is a floating-point number.
The point is what makes a float.



Take, for example, the speed of light, expressed in meters per second. Written directly it would look like this: 300000000.

To avoid writing out so many zeros, physics textbooks use an abbreviated form, which you have probably already seen: 3 x 108.
It reads: three times ten to the power of eight.
In Python, the same effect is achieved in a slightly different way - take a look:
3E8
The letter E (you can also use the lower-case letter e - it comes from the word exponent) is a concise record of the phrase times ten to the power of.
Note:
•the exponent (the value after the E) has to be an integer;
•the base (the value in front of the E) may be an integer



The first is a string, the second is a numerical literal (a float), the third is a numerical literal (an integer), and the fourth is a boolean literal.

Exercise 3
What is the decimal value of the following binary number?
1011
It's 11, because (2**0) + (2**1) + (2**3) = 11


We'll begin with the operators which are associated with the most widely recognizable arithmetic operations:
+, -, *, /, //, %, **

A**(double asterisk) sign is an exponentiation (power) operator. Its left argument is the base, its right, the exponent.
Classical mathematics prefers notation with superscripts, just like this: 23. Pure text editors don't accept that, so Python uses ** instead, e.g., 2 ** 3.

Remember: It's possible to formulate the following rules based on this result:
•when both ** arguments are integers, the result is an integer, too;
•when at least one ** argument is a float, the result is a float, too.



Operators and their priorities
So far, we've treated each operator as if it had no connection with the others. Obviously, such an ideal and simple situation is a rarity in real programming.
Also, you will very often find more than one operator in one expression, and then this presumption is no longer so obvious.
Consider the following expression:
2 + 3 * 5
You probably remember from school that multiplications precede additions.
You surely remember that you should first multiply 3 by 5 and, keeping the 15 in your memory, then add it to 2, thus getting the result of 17.
The phenomenon that causes some operators to act before others is known as the hierarchy of priorities.
Python precisely defines the priorities of all operators, and assumes that operators of a larger (higher) priority perform their operations before the operators of a lower priority.
So, if you know that * has a higher priority than +, the computation of the final result should be obvious.



Operators and their bindings
The binding of the operator determines the order of computations performed by some operators with equal priority, put side by side in one expression.
Most of Python's operators have left-sided binding, which means that the calculation of the expression is conducted from left to right.
This simple example will show you how it works. Take a look:
print(9 % 6 % 2) 

There are two possible ways of evaluating this expression:
•from left to right: first 9 % 6 gives 3, and then 3 % 2 gives 1;
•from right to left: first 6 % 2 gives 0, and then 9 % 0 causes a fatal error.

Run the example and see what you get.
The result should be 1. This operator has left-sided binding. But there's one interesting exception.


Shortcut operators
It's time for the next set of operators that make a developer's life easier.
Very often, we want to use one and the same variable both to the right and left sides of the = operator.
For example, if we need to calculate a series of successive values of powers of 2, we may use a piece like this:
x = x * 2
You may use an expression like this if you can't fall asleep and you're trying to deal with it using some good, old-fashioned methods:
sheep = sheep + 1
Python offers you a shortened way of writing operations like these, which can be coded as follows:
x 2 sheep 1

Let's try to present a general description for these operations.
If op is a two-argument operator (this is a very important condition) and the operator is used in the following context:
variable = variable expression
It can be simplified and shown as follows:
variable = expression
Take a look at the examples below. Make sure you understand them all.
i = i + 2 * j ⇒ i 2 * j
var = var / 2 ⇒ var 2
rem = rem % 10 ⇒ rem 10
j = j - (i + var + rem) ⇒ j (i + var + rem)
x = x ** 2 ⇒ x 2


INPUT FUNCTION
input()
print("Tell me anything...") 
anything = input() 
print("Hmm...", anything, "... Really?")

The input()function with an argument
The input() function can do something else: it can prompt the user without any help from print().
We've modified our example a bit, look at the code:
anything = print("Hmm...", anything, "...Really?") 
Note:
•the input() function is invoked with one argument - it's a string containing a message;
•the message will be displayed on the console before the user is given an opportunity to enter anything;
•input()will then do its job.

Type casting
Python offers two simple functions to specify a type of data and solve this problem - here they are: int() and float().
Their names are self-commenting:
•the int() function takes one argument (e.g., a string: int(string)) and tries to convert it into an integer; if it fails, the whole program will fail too (there is a workaround for this situation, but we'll show you this a little later);
•the float() function takes one argument (e.g., a string: float(string)) and tries to convert it into a float (the rest is the same).

leg_a = float(input("Input first leg length: ")) 
leg_b = float(input("Input second leg length: ")) 
print("Hypotenuse length is", (leg_a**2 + leg_b**2) ** .5) 

CODE
fnam = input("May I have your first name, please? ") 
lnam = input("May I have your last name, please? ") 
print("Thank you.") 
print("\nYour name is " + fnam + " " + lnam + ".")

OUTPUT
May I have your first name, please? Avni
May I have your last name, please? Maheshwari
Thank you.

Your name is Avni Maheshwari.

Three types of data types are:
1. Int
2. Float and,
3. Complex

print(type(x)

Typecasting

x=56

print(x,type(x))

y=str(x)

print(y,type(y))

z=bool(x)

print(z,type(z))

p=0

Boolean value are True and False.

If x = 1, print(bool(x) will be True
If x = 0, print(bool(x) will be False

Replication
The*(asterisk) sign, when applied to a string and number (or a number and string, as it remains commutative in this position) becomes a replication operator:
string * number 
number * string

It replicates the string the same number of times specified by the number.
For example:
• "James" * 3 gives "JamesJamesJames"
• 3 * "an" gives "ananan"
• 5 * "2" (or "2" * 5) gives "22222"(not10!)




This simple program "draws" a rectangle, making use of an old operator (+) in a new role:
print("+" + 10 * "-" + "+") 
print(("|" + " " * 10 + "|\n") * 5, end="") 
print("+" + 10 * "-" + "+")

	
Scenario
Your task is to prepare a simple code able to evaluate the end time of a period of time, given as a number of minutes (it could be arbitrarily large). The start time is given as a pair of hours (0..23) and minutes (0..59). The result has to be printed to the console.
For example, if an event starts at 12:17 and lasts 59 minutes, it will end at 13:16.

hour = int(input("Starting time (hours): "))
mins = int(input("Starting time (minutes): "))
dura = int(input("Event duration (minutes): "))

# Write your code here.
mins = mins + dura
hour = hour + mins // 60

print("Number of mins: ",mins)
print("Number of hours: ",hour)
print("End time will be: hour % 24 and mins % 60")
print(hour % 24, ":", mins % 60, sep="")

hour = int(input("Starting time (hours): "))
mins = int(input("Starting time (minutes): "))
dura = int(input("Event duration (minutes): "))

# Write your code here.
mins = mins + dura
hour = hour + mins // 60

print("Number of mins: ",mins)
print("Number of hours: ",hour)
print("End time will be: hour % 24 and mins % 60")
print(hour % 24, ":", mins % 60, sep="")


Key takeaways

1. The print() function sends data to the console, while the input() function gets data from the console.
2. The input() function comes with an optional parameter: the prompt string. It allows you to write a message before the user input, e.g.:
name = input() print("Hello, " + name + ". Nice to meet you!")

3. When the input() function is called, the program's flow is stopped, the prompt symbol keeps blinking (it prompts the user to take action when the console is switched to input mode) until the user has entered an input and/or pressed the Enter key

Tip: the above-mentioned feature of the input() function can be used to prompt the user to end a program. Look at the code 
name = input("Enter your name: ") 
print("Hello, " + name + ". Nice to meet you!") 
print("\nPress Enter to end the program.") 
input() 
print("THE END.")

3. The result of the input() function is a string. You can add strings to each other using the concatenation (+) operator. Check out this code:
num_1 = input("Enter the first number: ") # Enter 12 
num_2 = input("Enter the second number: ") # Enter 21 
print(num_1 + num_2) # the program returns 1221 

4. You can also multiply (* - replication) strings, e.g.:
my_input = input("Enter something: ") # Example input: hello 
print(my_input * 3) # Expected output: hellohellohello


The == (equal to) operator compares the values of two operands. If they are equal, the result of the comparison is True. If they are not equal, the result of the comparison is False.
Look at the equality comparison below - what is the result of this operation?
Var 0

The question will be as follows:
black_sheep 2 * white_sheep 
Due to the low priority of the == operator, the question shall be treated as equivalent to this one:
black_sheep (2 * white_sheep)

So, let's practice your understanding of the == operator now - can you guess the output of the code below?
var = 0 # Assigning 0 to var print(var 0) var = 1 # Assigning 1 to var print(var 0)

Print Multiple Variables
x= 5
y = 5.7
lang_name=”python scripting”
PRINT METHOD 1: print(x,y,lang_name)
PRINT METHOD 2: print(“ {} {} {}”.format(x,y,lang_name))   
OUTPUT::
$ python one.py 
(5, 5.6, 'python scripting')  METHOD 1
5.6 5 python scripting 	METHOD 2
The format function can also be used as: 
print(f“The value of s is {x} the value of y is {y} the value of z is {z}”)


EXAMPLE
x=2
y=3
z=4
print(f"The valule of x is:{x}, \nthe value of y is:{y} \nand the value of z is:{z}")

OUTPUT
The valule of x is:2, 
the value of y is:3 
and the value of z is:4


##Convert any input to any data type using eval function:
>> x = eval(input(”Enter a number”))
Enter a number 4.2
>> print(type(x)
<class ‘float> 

x=eval(input(“enter a number”))
y=eval(input(“enter antohe number”))
result=x+y
print(f"Addition of the numbers is {result} and the type is {type(result)}")



Inequality: the not equal to operator (!=)
The != (not equal to) operator compares the values of two operands, too. Here is the difference: if they are equal, the result of the comparison is False. If they are not equal, the result of the comparison is True.


var = 0 # Assigning 0 to var print(var 0) var = 1 # Assigning 1 to var print(var 0)


If you want to know if there are more black sheep than white ones, you can write it as follows:
black_sheep white_sheep # Greater than 


Using one of the comparison operators in Python, write a simple two-line program that takes the parameter n as input, which is an integer, and prints False if n is less than 100, and True if n is greater than or equal to 100.

n = int(input("Write a number: "))
print(n >= 100) #n is greater so True, if not then False
Write a number: 55
False



Conditions and conditional exectution
if true_or_not: 
	do_this_if_true

Printing strings in array

0 is the first index number of a string and -1 is the last index number of a string. 
>>my_variable=”python scripting” 
#now to print the first 5 characters of the word python, run:
>>print(my_variable[0:6])       (0-5 are 4 characters so we take 0:6)
#Print letter at the 0 index of a var x.
>> x=“Python is language”
>> print(x[0])
 
This is called slicing of strings.
To store the value of the about output to another variable, run
>>my_variable=”python scripting” 
>>print(my_variable[0:6])       
>>var_out=my_variable[0:6]
>>print(var_out)

Modify the value in a string using index numbers
Replace number 10 to 25 
>> x = [10,20,30]
>> x[0]=25
>> print(x)
[25,20,30]

Find the length of a string
>>my_variable=”python scripting” 
>>print(len(my_variable))       (len is the length function)

Concatenate two strings
# vi strings.py
>>var1="A good"
>>var2="day is today"
>>print(var1 +" "+ var2)
OUTPUT
avni@laptop:~$ python3 strings.py 
A good day is today

To replace a str in a var:  var.replace( )
var= ‘Python for beginners’
print(var.replace(‘beginners’, ‘Absolute beginners’))
## this will replace the word beginners with Absolute beginners. 
Replace using index numbers doesn’t work in strings. 

UPPER CASE AND LOWER CASE IN STRINGS

### Make a string in upper or lower case.
>> mystring=“Python Scripting”
>> print(mystring.lower())  (this will print the string in lower case)
python scripting
>> print(mystring.upper())   (this will print the string in upper case)
PYTHON SCRIPTING

### To find the number of available operations for a string.
>> x=“python”
>> print(dir(x))   (this will output all the available operations with this string)

'__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']

## print(variable.swapcase()) 
This will swap upper case letters to lower and vice-versa.

## print(mystring.title())  
this will capitalize all the first letters in the words.

## print(mystring.capitalize()) 
this will capitalize only the first letter of a word in a string.  

# Boolean result operations
To check a string using particular filters.
>> my_str= “python”
>> print(my_str.startswith(‘P’))  
False
This checks if the string starts with capital P, since it does not, the result is False. 

To check if a word is in a string, use in operator  {the output will be in boolean values(true or false)}
>>course= ‘Python for beginners’
>>print(‘Python’ in course) 
True
>>course= ‘Python for beginners’
>>print(‘python’ in course)
False   (case sensitive – ‘p’ and ‘P’)
 
More operations are:
print(my_str.endswith(‘P’))  (is the line endswith the letter/word)
print(my_str.islower())  (is the line is in lower case or not)
print(my_str.isupper())   (is the line in upper case or not)
print(my_str.istitle())   (is the first letter capital or not)
print(my_str.isalpha())   (is the str in all alphabets {space bw words is not considered alpha})
print(my_str.isnumeric())   (is the str numeric or not)

### To get more operations, run 
>> help(str)     >> help(int)    >>help(float)


Join center and zfill (zero fill)

To separate the letters in a word using differ separators. 
>> x=”python”
>> print(“-”.join(x))
p-y-t-h-o-n

>> print(“*”.join(x))
p*y*t*h*o*n
>> print(“\t”.join(x))
p       y       t       h       o       n


Align str in the center with some numerical spacing

This aligns the string in the center with numerical spaces
>> my_str=”python”
>> my_str1=”bash scripting”
>> print(my_str.center(20))
       python       
>>print(my_str.center(20)+”\n”+my_str1.center(20))
	 python       
   bash scripting

zfill (zero fill)
zfill fills 0 towards the left of the string. 
>> my_str=”python”
>> print(my_str.zfill(10))
Python consist of 6 letters and we mentioned zfill(10) so zfill will add 4 zeros at the starting of my_str and then python will be added. 

Like this: 0000python 


STRIP AND SPLIT OPERATIONS
>> my_str=“   python    ”    
>> print(my_str.strip())  (This will remove the extra space on the sides of the str python) 

To remove a letter/word from the rigth or left side of a sentence, RUN
>> my_str=“python”    
>> print(my_str.strip(‘n’))   (here I want to remove letter ‘n’  )

Remove from right side, RUN
>> print(my_str.rstrip(‘n’))			(my_str.rstrip())
Remove from left side, RUN
>> print(my_str.lstrip(‘n’))			(my_str.lstrip())   


SPLIT OPERATION
It will split the sentence into a comma (,) based sequence of items. 
>> print(my_str.split())
>> my_str=”python is easy”
>> print(my_str.split())
[‘python’, ‘is’, ‘easy’] 


COUNT OPERATION
It will count a letter/word in a string.
>> my_str=”python is easy”
>> print(my_str.count(‘is’))   				(it counts the number of times letter “is” is in the string and prints the number)
1

FIND THE POSITION OF A LETTER
>> x=“python is easy”
>> print(x.index(‘is’))		(it will print the position of the letter in the strng)
7 
x.find()  will also find the position of the letter.
>> print(x.find(‘is’))		(it will print the position of the letter in the strng)
7 

CENTER, LEFT AND RIGHT ALIGN STRING
To center align, RUN
>> x=“Hello world”
>> print(x.center(width))  (here width will be a number, width is the number of columns in your terminal)
>> print(x.center(220)) 
Linux command to find the number of colums, RUN
avni@laptop: ~$ tput cols (this will print the number of cols as per the size of the terminal)

>> print(x.center(122))
To right align, RUN
>> print(x.rjust(122))
To left align, RUN
>> print(x.ljust(122))

To find the memory location of a variable, RUN,
>> x=5
>> print(id(x))   (the id function will give the memory location of the var x)
1402980498120


Clear your function for an object.
>> x=[10,20,2030,40,40]
>> print(x)
[10,20,2030,40,40]  ---> output before function
>> x.clear()   (var.clear() function clears a list) 
>> print(x)
[]   ---> output after function





Change the ID memory block/location of your variable.  var.copy( ) 
>> var=[1,2,3,4e53453]
>> newvar=var
>> nvar=var.copy( )
>> print(id(var), id(newvar))
>> print(id(nvar))
140502265766448 140502265766448
140502265769008
WHENEVER YOU ARE MODIFYING YOUR LIST, DON’T DO IT WITH print function.

Insert Append number in a var
>> my_list=[5,4,6,3,6,3]
>> print(my_list)
[5,4,6,3,6,3]
>> my_list.append(56)       { var.append() adds a number at the end of a list}
>> print(my_list)
[5, 4, 5, 3, 4, 56]

Insert
>> my_list.insert(1,24)  	{ var.insert(index,number_to_replace) – this replaces number at the index number mentioned }
>> print(my_list)
[5, 24, 4, 5, 3, 4]

Extend var.extend()
>> my_new_list=[45,64]
>> mylist.extend(my_new_list)
>> print(mylist) 
[5, 4, 5, 3, 3, 45, 64]


Remove var.remove(x)
>> my_list=[5,4,6,3,3,4,34,37]
>> print(my_list)
>> my_list.remove(3)
>> print(my_list)
[5, 4, 6, 3, 3, 4, 34, 37]
[5, 4, 6, 3, 4, 34, 37]


Pop var.pop()
This removes the last item in the list. 
Removes number at the index place if specified. 

my_list=[5,4,6,3,3,4,34,37]
my_list.pop()
print(my_list)
[5, 4, 6, 3, 3, 4, 34]   (it removed the last number ‘37’)

Reverse var.reverse()
This prints the list in reverse order.
my_list=[5,4,6,3,3,4,34,37]
my_list.reverse()
print(my_list)
[37,34,4,3,3,6,5,4]


sort var.sort()
Arranges data in ascending order
my_list.sort()
print(my_list)

To arrange in descending order, RUN


my_list.sort()
my_list.reverse()
print(my_list)
OR
my_list.sort(reverse=True)
print(my_list)

Tuple

Tuple start with ( ) 
var1=(1,2,25,2,53)    ----> this is a tuple
var2=[1,2,32,35,34]   -----> this is list
var3=(1,2,43,[3,34,3],345,3)   ----> this is a list within a tuple
var4=()   ----> this is an empty tuple

Access value within a tuple
Print 34 from the list within the tuple. 
var3=(1,2,43,[3,34,3],345,3)
print(var3[3][1])    (print(var[tuple_index_no.][index_no._within_list])

34   ----> output

Tuples are immutable, the values inside a tuple cannot be changed. Tuple object doesn’t support item assignment.



Dictionary
It is represented by { } 
Values in a dictionary are entered in a key:value pair format.
Ex: mydict={‘color’:’blue’,’size’:’34’,’length’:’90’}
All the strings should be in quotes. 

Add a new key:value pair to the variable
mydict[‘three’]=3
print(mydict)
Output .....

To replace a value to existing key, RUN
mydict[‘three’]=53
print(mydict)

To get a list of all the keys, RUN	keys()

print(mydict.keys()) 

To get a list of all the values, RUN   values()

print(mydict.values())

To print the items from a dictionary, RUN  items()

print(mydict.items())

To add new data to an old dictionary, RUN  update()

mynewdict={‘four’:4}
mydict.update(mynewdict)
print(mydict)
{'color': 'blue', 'size': 34, 'length': 90, 'four': 4}

To pop/remove a key-value pair from a dictionary, RUN
var.pop(key)  pop(x)
mydict.pop(‘size’)
print(mydict)

removed_item=mydict.pop('size')
print(removed_item)


To remove an item (key-value pair) from a dictionary, RUN 
var.popitem()  - it will randomly remove an item from the list, mostly the last one. popitem()
removed_item=mydict.popitem()

print(f"The item removed from {mydict} is {removed_item}")

Create a dictionary using a list of keys. dict.fromkeys()

keys=['a','e','i','o','u']		(list of keys)		
mydict=dict.fromkeys(keys)		(defining new var “mydict” with fn dict.fromkeys(var)
print(f"Keys without values{mydict}")
mydict['a']='Apple'  	(assigning value to key ‘a’)
print(f'Keys with values{mydict}')


Add another key to a dictionary  setdefault()

LOGICAL OPERATORS

and (this returns True if both the expressions returns true)
or (this returns True if either one of the expresssions returns true)
not (this inverses the value which we give)

>>> price = 25
>>> print(price > 10)
True

>>> print(price > 10 and price < 30) {and operator}
True

>>> print(price > 10 or price < 30) {or operator}
True

>>> print(not price > 10) {not operator}
False

IF ELSE STATEMENT
price = 30
if price > 25:
	print(“The price is higher”)
else:
	print(“The price is reasonable.”)

IF ELIF ELSE STATEMENT

price = 30
if price > 25:
	print(“The price is higher”)
elif price <= 15:
	print(“Can be considered.”)
elif price < 10:
	print(“Let’s make a purchase.”)
else:
	print(“Will buy another time.”)


RANGE FUNCTION

numbers=range(15) #this prints numbers from 0 to 15
for i in numbers:
    print(i)

numbers=range(15,20) #this prints numbers from 15 to 20
for i in numbers:
    print(i)

numbers=range(15,20,2) #this prints numbers from 15 to 20 with a gap of 2 numbers - 15,17,19
for i in numbers:
    print(i)




Round function: print(round(var))
Rounds a floating point number to an integer.

X = 2.9
print(round(x))
3

Abs function: print(abs(<negt_value>))
It returns a positive number
print(abs(-2.9))
2.9

Modules
import math #import a module to use its functions

print(math.floor(2.9))


print(math.ceil(2.9))

WHILE LOOPS IN PYTHON

# While Loops
'''
while condition: # until this is true, the below code will exec repeatedly 
    ...  # this will be exec repeatedly
'''
# Example (remove the ''' to run the below code) 

i = 1
while i <= 5:
    print(i)
    i = i + 1  #(we need to add 1 to i or else the value of i will always be 1 and the loop      will never stop)
print("Done")

print("*-*-" * 20)

i = 1
while i <= 500:
    print(i)
    i += 1

print("*-*-" * 20)

i = 10
while i >= 1:
    print(i * " * ")
    i -= 1

print("*-*-" * 20)

i = 1
while i <= 10:
    print(i * "*")
    i += 1

GUESS GAME
secret_num=9
guess_count = 0
guess_limit = 3
while guess_count < guess_limit:
    guess = int(input("Guess: "))
    guess_count += 1
    if guess == secret_num:
        print("You won!")
        break         --> this breaks the loop if the above condition was True.
Else:      --> this is the Else block of a while loop
    print('Sorry, you failed!')


# Car game

help = "start - to start the car \nstop - to stop the car \nquit - to exit"
start = "Car started... Ready to go!"
stop = "Car stopped!"
ipt = ""
started = False
while True:
    ipt = input("> ").lower()
    if ipt == "start":
        if started:
            print("Car is already started.")
        else:
            started = True
            print(start)
    elif ipt == "stop":
        if not started:
            print("Car is already stopped!!!")
        else:
            started = False
            print(stop)
    elif ipt == "help":
        print(help)
    elif ipt == "quit":
        print("Thank you for playing.")
        break
    else:
        print("Sorry, I don't understand that..")
--------------------------------------------------------------------------------


2D Lists – each item in a list is another list. 
For eg: list = [1 ,2 ,4 ,5]
1 = [That is 




