# 1-assignment-19


6
I noticed that some numpy operations take an argument called shape, such as np.zeros, whereas some others take an argument called size, such as np.random.randint. To me, those arguments have the same function and the fact that they have different names is a bit confusing. Actually, size seems a bit off since it really specifies the .shape of the output.

Is there a reason for having different names, do they convey a different meaning even though they both end up being equal to the .shape of the output?

python
numpy
Share
Improve this question
Follow
edited Oct 22, 2018 at 9:34
asked Jun 28, 2017 at 14:11
user avatar
P-Gn
21.2k66 gold badges8080 silver badges9797 bronze badges
4
I don't think so. Its community developed. Its not always easy to ensure consistency. I agree with you. Shape (in the numpy context) seems to me the better option for an argument name. The actual relation between the two is size = np.prod(shape) so the distinction should indeed be a bit more obvious in the arguments names. – 
armatita
 Jun 28, 2017 at 14:20
1
randint uses the size parameter name, but uses shape in the explanation. This is not to be confused with a real size attribute. – 
hpaulj
 Jun 28, 2017 at 16:36
I would suggest you to change the title to better reflect the fact that you talk about the argument names and not the attributes. – 
Mayou36
 Oct 20, 2018 at 11:40
@Mayou36 Good suggestion. Done. – 
P-Gn
 Oct 22, 2018 at 9:34
Why is no answer accepted? – 
Ramanujan
 Feb 16, 2020 at 23:02
Show 2 more comments
2 Answers
Sorted by:

Highest score (default)

10

Shape relates to the size of the dimensions of an N-dimensional array.

Size regarding arrays, relates to the amount (or count) of elements that are contained in the array (or sometimes, at the top dimension of the array - when used as length).

For example, let a be a matrix

1  2  3  4
5  6  7  8
9 10 11 12
the shape of a is (3, 4), the size of a is 12 and the size of a[1] is 4.

Share
Improve this answer
Follow
edited Jun 28, 2017 at 14:25
answered Jun 28, 2017 at 14:18
user avatar
Uriel
14.8k66 gold badges2323 silver badges4646 bronze badges
9
I think the OP understands that. He/She is questioning the choice of names for the arguments. For example randint asks for a size (int) but can actually take tuples (which in numpy is typically interpreted as a shape). – 
armatita
 Jun 28, 2017 at 14:22
I think we could say that a.shape.prod() = a.size – 
Euler_Salter
 Aug 2, 2018 at 9:06
1
@Euler_Salter, yes, but that's not the question. The question is about the argument names shape and size. And in the argument, they serve the same purpose and do not adhere to the relationship you pointed out. (they adhere to shape == size) – 
Mayou36
 Oct 20, 2018 at 11:37
Add a comment

1

Because you are working with a numpy array, which was seen as a C array, size refers to how big your array will be. Moreover, if you can pass np.zeros(10) or np.zeros((10)). While the difference is subtle, size passed this way will create you a 1D array. You can give size=(n1, n2, ..., nn) which will create an nD array.

However, because python users want multi-dimensional arrays, array.reshape allows you to get from 1D to an nD array. So, when you call shape, you get the N dimension shape of the array, so you can see exactly how your array looks like.

In essence, size is equal to the product of the elements of shape.

EDIT: The difference in name can be attributed to 2 parts: firstly, you can initialise your array with a size. However, you do not know the shape of it. So size is only for total number of elements. Secondly, how numpy was developed, different people worked on different parts of the code, giving different names to roughly the same element, depending on their personal vision for the code.

Share
Improve this answer
Follow
edited Jun 28, 2017 at 14:35
answered Jun 28, 2017 at 14:23
user avatar
Marian D
3944 bronze badges
I'm not sure what you're trying to explain with the np.zeros(10) vs np.zeros((10)) difference. Did you mean np.zeros((10, )) (that is, the second one is actually a tuple)? – 
alichaudry
 Jul 17, 2018 at 22:09
Add a comment
Your Answer
Sign up or log in
Post as a guest
Name
Email
Required, but never shown

By clicking “Post Your Answer”, you agree to our terms of service, privacy policy and cookie policy

Not the answer you're looking for? Browse other questions tagged python numpy or ask your own question.
The Overflow Blog
Ethical AI isn’t just how you build it, it’s how you use it
How a very average programmer became GitHub’s CTO (Ep. 447)
Featured on Meta
Announcing the arrival of Valued Associate #1214: Dalmarus
Improvements to site status and incident communication
Staging Ground: Reviewer Motivation, Scaling, and Open Questions
Collectives Update: Introducing Bulletins
Retiring Our Community-Specific Closure Reasons for Server Fault and Super User
The [social] tag is in the process of being burninated
Related
2222
Calling a function of a module by using its name (a string)
2877
How do I change the size of figures drawn with Matplotlib?
3665
Using global variables in a function
582
Is there a NumPy function to return the first index of something in an array?
3022
How to make function decorators and chain them together?
716
How can the Euclidean distance be calculated with NumPy?
794
How to print the full NumPy array, without truncation?
711
Dump a NumPy array into a csv file
637
Convert pandas dataframe to NumPy array
563
Most efficient way to map function over numpy array
Hot Network Questions
Was Rishi Vashishta born to a prostitute?
Is it true that the type of ML model used is irrelevant?
Calculate Opamp output
Could a spacecraft theoretically fly a smooth, curved arc of a turn in space like an aircraft?
Which place in the car is coolest on hot sunny days?
Why are binary extension fields preferred for Shamir secret sharing?
As an editor, what to do when a referee recommends citing their own papers?
Where to find papers when Google Scholar and libraries fail?
Is paralleling MOSFETs a good or a bad idea?
Is there an algorithm or graph theory that allows me to not need to store an intermediate matrix when calculating AT*Y1*A + BT*Y2*B?
What's the best die to roll?
Are the computers on Pioneer 10 & 11 still running?
Updating WordPress core with zero downtime - I mean zero
On entire functions with polynomial Schwarzian derivative
ReadOnly queries on secondary server do not return correct values
What does "the money was the chips" mean?
A capacitor charge time - two methods two different answers
Torque wrench not clicking anticlockwise
Cyristal Disk Info: Total Host Writes Shows Two Distinct Values
How to XOR two expressions of `test`?
What is the next word in this long sequence?
Why compiling errors disappear after deleting cache?
When playing from a fake book, how strict should I be about the root note?
What is the first animated cartoon?
 Question feed

STACK OVERFLOW
Questions
Help
PRODUCTS
Teams
Advertising
Collectives
Talent
COMPANY
About
Press
Work Here
Legal
Privacy Policy
Terms of Service
Contact Us
Cookie Settings
Cookie Policy
STACK EXCHANGE NETWORK
Technology
Culture & recreation
Life & arts
Science
Professional
Business
API
Data
Blog
Facebook
Twitter
LinkedIn
Instagram
Site design / logo © 2022 Stack Exchange Inc; user contributions licensed under cc by-sa. rev 2022.5.31.42254

Your privacy
NumPy to treat arrays of different shapes during arithmetic operations. Arithmetic operations on arrays are usually done on corresponding elements. If two arrays are of exactly the same shape, then these operations are smoothly performed.

Example 1
 Live Demo
import numpy as np 

a = np.array([1,2,3,4]) 
b = np.array([10,20,30,40]) 
c = a * b 
print c
Its output is as follows −

[10 40 90 160]
If the dimensions of two arrays are dissimilar, element-to-element operations are not possible. However, operations on arrays of non-similar shapes is still possible in NumPy, because of the broadcasting capability. The smaller array is broadcast to the size of the larger array so that they have compatible shapes.

Broadcasting is possible if the following rules are satisfied −

Array with smaller ndim than the other is prepended with '1' in its shape.

Size in each dimension of the output shape is maximum of the input sizes in that dimension.

An input can be used in calculation, if its size in a particular dimension matches the output size or its value is exactly 1.

If an input has a dimension size of 1, the first data entry in that dimension is used for all calculations along that dimension.

A set of arrays is said to be broadcastable if the above rules produce a valid result and one of the following is true −

Arrays have exactly the same shape.

Arrays have the same number of dimensions and the length of each dimension is either a common length or 1.

Array having too few dimensions can have its shape prepended with a dimension of length 1, so that the above stated property is true.

The following program shows an example of broadcasting.

Example 2
 Live Demo
import numpy as np 
a = np.array([[0.0,0.0,0.0],[10.0,10.0,10.0],[20.0,20.0,20.0],[30.0,30.0,30.0]]) 
b = np.array([1.0,2.0,3.0])  
   
print 'First array:' 
print a 
print '\n'  
   
print 'Second array:' 
print b 
print '\n'  
   
print 'First Array + Second Array' 
print a + b
The output of this program would be as follows −

First array:
[[ 0. 0. 0.]
[ 10. 10. 10.]
[ 20. 20. 20.]
[ 30. 30. 30.]]

Second array:
[ 1. 2. 3.]

First Array + Second Array
[[ 1. 2. 3.]
[ 11. 12. 13.]
[ 21. 22. 23.]
[ 31. 32. 33.]]
The following figure demonstrates how array b is broadcast to become compatible with a.

array
1| SciPy (Scientific Numeric Library)
Officially released in 2000-01, SciPy is free and open source library used for scientific computing and technical computing. The library consists of modules for optimisation,

image processing, FFT, special functions and signal processing.

The SciPy package includes algorithms and functions which are the crux of Python scientific computing capabilities. The sub-package includes: 

  io: used for the standard input and output
lib: this function is used to wrap python external libraries
signal: used for processing signal tools
sparse: used for algorithms related to sparse matrix
spatial: widely used to determine paths in KD-trees, nearest neighbor and distance functions.
optimise: used to optimise algorithms which include linear programming.
linals: used for the regular linear algebra applications.
interpolate: used for the integration of tools
intergate: applied for integration of numerical tools
fftpack: this subpackage helps for the discretion Fourier to transform algorithms
cluster: the package consists of hierarchical clustering, vector quantisation, and K-means.
misc: used for the miscellaneous utility applications.
special: used to switch in special functions.
weave: a tool to convert C/C++ codes to python programming.
ndimage: used for wide range of functions in multi-dimensional image processing.
stats: used for better understanding and analysing of statistical functions.
constants: this algorithm includes physical specification and conversion components.
2| Pandas (Data Analytics Library)
Pandas is the most important data analysis library of Python. Being open source, it is used for analysing data with Python. It can take data formats of CSV or TSV files, or a SQL database and convert it into Python data frames with rows and columns which is similar to tables in statistical formats. The package makes comparisons with dictionaries with the aid of ‘for’ loops which are very easy to understand and operate.

Python 2.7 and above versions are required to install Pandas package. We need to import the Panda’s library into the memory to work with it. The following codes can be run to implement different operations on pandas.

  Import pandas as pd (importing pandas library to memory), it is highly suggested to import the library as pd because next time when we want to use the application we need not mention the package full name instead we can name as pd, this avoids confusion.
pd.read_filetype() (to open the desired file)
pd.DataFrame() (to convert a specified python object)
df.to_filetype (filename) (to save a data frame you are currently working with)
The advantage of using Pandas is that it can perform a bunch of functions on the tables we have created. The following are some functions that can be performed on selected data frames.

 df.median()-to get the median of each column
df.mean()-to get the mean of all columns
df.max()-to get the highest value of a column
df.min()-to get the minimum value of a column
df.std()-to get the standard deviation of each column.
df.corr()-to specify the relationship between columns of a data frame.
df.count()-to get the number of non-null values in each column of the data frame.
3| IPython (Command Shell)
Developed by Fernando Perez in the year 2001, IPython is a command shell which is designed for interactive calculation in various programming languages. It offers self-examination, rich media, shell syntax, tab completion, and history.

IPython is a browser-based notebook interface which supports code, text, mathematical expressions, inline plots and various media for interactive data visualisation with the use of GUI (Graphic User Interface) toolkits for flexible and rectifiable interpreters to load into one’s own projects.

IPython architecture contributes to parallel and distributed computing. It facilitates for the enhanced parallel applications of various styles of parallelism such as:

Customer user defined prototypes
Task Parallelism
Data Parallelism
Message cursory using M.P.I (Message Passing Interface)
Multiple programs, multiple data (MIMD) parallelism
A single program, multiple data (SPMD) parallelism
4| Numeric Python (Fundamental Numeric Package)
Better known as Numpy, numeric Python has developed a module for Python, mostly written in C.  Numpy guarantees swift execution as it is accumulated with mathematical and numerical functions.

Robust Python with its dynamic data structures, efficient implementation of multi-dimensional arrays and matrices, Numpy assures accurate calculations with matrices and arrays.

We need to import Numpy into memory to perform numerical operations.

Import numpy as np (to import Numpy into memory)
A_values=[20,30,40,50] (defining a list)
A=np.array(A_values) (to convert list into one dimensional numpy array)
print(A) (to get one dimensional array displayed)
print(A*9/5 +32) (to turn values in the list into degrees fahrenheit)
5| Natural Language Toolkit (Library For Mathematical And Text Analysis)
Simply known as NLP, Natural Language Processing library is used to build applications and services that can understand and analyse human languages and data. One of the sub-libraries which are widely used in NLP is NLTK (Natural Language Toolkit). It has an active discussion forum through which they give hands-on guidance on programming basic topics such as computational linguistics, comprehensive API documentation, linguistics to engineers, students, industries and researchers. NLTK is an open source free community-driven project which is accessible for operating systems such as Windows, MAC OS X, and Linux. The implementations of NLP are:

 Search engines (eg: Yahoo, Google, firefox etc) they use NLP to optimise the search results for users.
Social websites like Facebook, Twitter use NLP for the news feed. The NLP algorithms understand the interests of the users and show related posts.
Spam filters: unlike the traditional spam filters, the NLP has driven spam filters to understand what the mail is about and decides whether it is a spam or not.
NLP includes well known and advanced sub-librari
es which are very effective in mathematical calculations.
NumPy introduces a simple file format for ndarray objects. This .npy file stores data, shape, dtype and other information required to reconstruct the ndarray in a disk file such that the array is correctly retrieved even if the file is on another machine with different architecture.

numpy.save()
The numpy.save() file stores the input array in a disk file with npy extension.

import numpy as np 
a = np.array([1,2,3,4,5]) 
np.save('outfile',a)
To reconstruct array from outfile.npy, use load() function.

import numpy as np 
b = np.load('outfile.npy') 
print b 
It will produce the following output −

array([1, 2, 3, 4, 5])
The save() and load() functions accept an additional Boolean parameter allow_pickles. A pickle in Python is used to serialize and de-serialize objects before saving to or reading from a disk file.

savetxt()
The storage and retrieval of array data in simple text file format is done with savetxt() and loadtxt() functions.

Example
import numpy as np 

a = np.array([1,2,3,4,5]) 
np.savetxt('out.txt',a) 
b = np.loadtxt('out.txt') 
print b 
It will produce the following output −

[ 1. 2. 3. 4. 5.]
The savetxt() and loadtxt() functions accept additional optional parameters such as header, footer, and delimiter
The numpy module of Python provides a function called numpy.empty(). This function is used to create an array without initializing the entries of given shape and type.

Just like numpy.zeros(), the numpy.empty() function doesn't set the array values to zero, and it is quite faster than the numpy.zeros(). This function requires the user to set all the values in the array manually and should be used with caution.

Syntax
numpy.empty(shape, dtype=float, order='C')  
Parameters:
shape: int or tuple of ints

This parameter defines the shape of the empty array, such as (3, 2) or (3, 3).

dtype: data-type(optional)

This parameter defines the data type, which is desired for the output array.

order: {'C', 'F'}(optional)

This parameter defines the order in which the multi-dimensional array is going to be stored either in row-major or column-major. By default, the order parameter is set to 'C'.

Returns:
This function returns the array of uninitialized data that have the shape, dtype, and order defined in the function.

Example 1:
import numpy as np  
x = np.empty([3, 2])  
x  
Output:

array([[7.56544226e-316, 2.07617768e-316],
       	[2.02322570e-316, 1.93432036e-316],
       	[1.93431918e-316, 1.93431799e-316]])
In the above code

We have imported numpy with alias name np.
We have declared the variable 'x' and assigned the returned value of the np.empty() function.
We have passed the shape in the function.
Lastly, we tried to print the value of 'x' and the difference between elements.
Example 2:
import numpy as np  
x = np.empty([3, 3], dtype=float)  
x  
Output:

array([[ 2.94197848e+120, -2.70534020e+252, -4.25371363e+003],
       	[ 1.44429964e-088,  3.12897830e-053,  1.11313317e+253],
       	[-2.28920735e+294, -5.11507284e+039,  0.00000000e+000]])
Example 3:
import numpy as np  
x = np.empty([3, 3], dtype=float, order='C')  
x  
Output:

array([[ 2.94197848e+120, -2.70534020e+252, -4.25371363e+003],
       	[ 1.44429964e-088,  3.12897830e-053,  1.11313317e+253],
       	[-2.28920735e+294, -5.11507284e+039,  0.00000000e+000]]) 
In the above code

We have imported numpy with alias name np.
We have declared the variable 'x' and assigned the returned value of the np.empty() function.
We have passed the shape, data-type, and order in the function.
Lastly, we tried to print the value of 'x' and the difference between elements.
In the output, it shows an array of uninitialized values of defined shape, data type, and order.

Example 4:
import numpy as np  
x = np.empty([3, 3], dtype=float, order='F')  
x  
Output:

array([[ 2.94197848e+120,  1.44429964e-088, -2.28920735e+294],
       	[-2.70534020e+252,  3.12897830e-053, -5.11507284e+039],
       	[-4.25371363e+003,  1.11313317e+253,  0.00000000e+000]])


← PrevNext →

Youtube For Videos Join Our Youtube Channel: Join Now
Feedback
Send your Feedback to feedback@javatpoint.com
Help Others, Please Share
facebook twitter pinterest

 

Learn Latest Tutorials
Splunk tutorial
Splunk

SPSS tutorial
SPSS

Swagger tutorial
Swagger

T-SQL tutorial
Transact-SQL

Tumblr tutorial
Tumblr

React tutorial
ReactJS

Regex tutorial
Regex

Reinforcement learning tutorial
Reinforcement Learning

R Programming tutorial
R Programming

RxJS tutorial
RxJS

React Native tutorial
React Native

Python Design Patterns
Python Design Patterns

Python Pillow tutorial
Python Pillow

Python Turtle tutorial
Python Turtle

Keras tutorial
Keras


Preparation
Aptitude
Aptitude

Logical Reasoning
Reasoning

Verbal Ability
Verbal Ability

Interview Questions
Interview Questions

Company Interview Questions
Company Questions


Trending Technologies
Artificial Intelligence Tutorial
Artificial Intelligence

AWS Tutorial
AWS

Selenium tutorial
Selenium

Cloud Computing tutorial
Cloud Computing

Hadoop tutorial
Hadoop

ReactJS Tutorial
ReactJS

Data Science Tutorial
Data Science

Angular 7 Tutorial
Angular 7

Blockchain Tutorial
Blockchain

Git Tutorial
Git

Machine Learning Tutorial
Machine Learning

DevOps Tutorial
DevOps


B.Tech / MCA
DBMS tutorial
DBMS

Data Structures tutorial
Data Structures

DAA tutorial
DAA

Operating System tutorial
Operating System

Computer Network tutorial
Computer Network

Compiler Design tutorial
Compiler Design

Computer Organization and Architecture
Computer Organization

Discrete Mathematics Tutorial
Discrete Mathematics

Ethical Hacking Tutorial
Ethical Hacking

Computer Graphics Tutorial
Computer Graphics

Software Engineering Tutorial
Software Engineering

html tutorial
Web Technology

Cyber Security tutorial
Cyber Security

Automata Tutorial
Automata

C Language tutorial
C Programming

C++ tutorial
C++

Java tutorial
Java

.Net Framework tutorial
.Net

Python tutorial
Python

List of Programs
Programs

Control Systems tutorial
Control System

Data Mining Tutorial
Data Mining

Data Warehouse Tutorial
Data Warehouse




.
