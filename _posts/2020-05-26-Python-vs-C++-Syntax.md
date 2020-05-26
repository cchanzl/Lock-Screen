---
layout: post
title: "Python vs C++ Syntax"
category: python
date: 2020-05-26
---

Having started my programming journey with a lower-level language like C++, moving to Python should reasonably be reasonably efficient. Afterall, Python does away with the need to declare types at the outset, allowing for greater flexibility. The introduction of dictionaries also eliminated the need to create user-defined classes such as token, as i was taught in the <a href="https://cchanzl.github.io/tableau/2020/05/01/C++-Calculator-Solution">C++ Calculator Solution. </a>

However, when it comes to Python's syntax, 3 main differences stood out for me which i would summarise below. 

These 3 syntax differences are discussed in greater detail in the book "Learning Python, Fifth Edition" by Mark Lutz at the start of Chapter 10. This is a book that I would strongly recommend to any beginner when starting their Python journey.

<b> Parentheses are optional </b>


<b> End-of-line is end of statement </b>
The first thing i noticed when i first looked at Python's syntax was the lack of semicolons (";") at end of each statement. This came as a surprise - How would the compiler know when a statement would end?!. Well, the general rule as i realised is that the end of a line <b>automatically</b> terminates the statement. If i were to start programming with Python as my first language, this probably wouldn't look so weird. One advantage of learning C++ is that it allows me to appreciate finer details such as this that I would have otherwise missed as a novice.

Of course, there are exceptions to this general rule, such as when you require multiple statements on a single line where semicolons are required as statement separators.

<b> End of indentation is end of block </b>
