---
layout: post
title: "Python Calculator"
category: python
date: 2020-05-29
---

The first program that really helped me to learn C++ was the <a href="https://cchanzl.github.io/tableau/2020/05/01/C++-Calculator-Solution">solution to the calculator exercise. </a> The purpose of the program would be familiar to most beginners, hence making it easy to understand. Yet, it challenges the notion of how we understand calculators work from a coding perspective. Simple issues like reading each character of input and differentiating the types and order of operations was something I took for granted.

So i thought this would be a good first task when learning Python as well, to code a similar program based on the grammar of the C++ solution. Due to the differences in syntax, particularly the use of dynamic typing in Python, a different approach is required. I elaborate further on some of the main difficulties i faced below.

<b> Lack of type sensitive input operation in Python </b>
<br>

In the C++ solution, inputs to the program are bound to a certain type due to the operation of cin. This binding allows numeric inputs to be identified as double and non-numeric inputs (such as "(" and "/") to be identified as character type. In Python, this is achieved first by reading the inputs into a list. I then defined dictionary() to filter the inputs accordingly. For example, when "55+6;" is entered, list_expr will be assigned to {"5", "5", "+", "6"}. Dictionary() will then iterate through the list, combining successive integers to form "55".

zip() is then used to create a dictionary of the inputs. This is the Python equivalent of the token class execution in the C++ solution, with list_keys.pop() being the get() and list_keys.append() being the putback() equivalent.

Error and exception handling have not been built into the code yet. This is definitely something I should pick up again in another post as there are many ways the code can break with different inputs at the moment. But it is working as a proof of concept.

<b> Scoping, Scoping and Scoping </b>
<br>

The use of the token class in C++ means that a global variable is required in the Python version as well (at this stage anyway without involving user-defined classes in Python). This takes the form of dict_expr and list_keys, both of which are fundamental in the code, being reference in expression(), term() and primary(). 

There are also multiple occasions where I used local variables, such as t, a, x and y for iteration purposes. This caused some issues in the beginning and probably not best practice so there is room for improvement here.

<b> Lists, Sets and Dictionaries are your best friend </b>
<br>

Understanding the syntax, expressions and methods of lists, sets and dictionaries is crucial here. The ability of sets to allow comparisons of overlapping members is fundamental to how dictionary() works. Future improvement can also be easily allowed for by adding members into char_set, for example to include functionality for factorial calculations. At the start, I struggled with the slicing operation within dictionary() with the error "TypeError: can only assign an iterable" for a good hour before realising that X[0:2] = 1 does not work as "1" is not an iterable. X[0:2] = [1] works as s list slice must be filled by a list. I guess this is part of the learning process.

<script src="https://gist.github.com/cchanzl/e0ee6e6835e352c64f17f60fc79138b7.js"></script>
