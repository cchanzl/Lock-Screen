---
layout: post
title: "Python vs C++ Syntax"
category: python
date: 2020-05-16
---

Having started my programming journey with a lower-level language like C++, moving to Python should be reasonably efficient. Afterall, Python does away with the need to declare types at the outset, allowing for greater flexibility. The introduction of dictionaries also eliminated the need to create user-defined classes such as token, as i was taught in the <a href="https://cchanzl.github.io/tableau/2020/05/01/C++-Calculator-Solution">C++ Calculator Solution. </a>

However, when it comes to Python's syntax, 3 main differences stood out for me which i summarise below. 

These 3 syntax differences are discussed in greater detail in the book "Learning Python, Fifth Edition" by Mark Lutz at the start of Chapter 10. I would strongly recommend this book to any beginner when starting their Python journey.

<b> Parentheses are optional </b>
<br>

Including parenthese when typing out formulas has become sort of a second habit, having worked primarily on Excel throughout my whole career. Formulas such as =sum(), =vlookup() and =indirect() makes sense. This made sense when i started out on C++ as well, happily wrapping for() and while() loop's arguments within (). In Python, parentheses are not strictly necessary (in some cases) for expressions although it would still run fine including them. I would note that in other ways, parentheses are absolutely necessary, such as enclosing arguments in a type-specifc method method like sorted() or count(). 

<b> End-of-line is end of statement </b>
<br>

The first thing i noticed when i first looked at Python's syntax was the lack of semicolons (";") at end of each statement. This came as a surprise - How would the compiler know when a statement would end?! Well, the general rule as i realised is that the end of a line <b>automatically</b> terminates the statement. If i were to start programming with Python as my first language, this probably wouldn't look so weird. One advantage of learning C++ is that it allows me to appreciate finer details such as this that I would have otherwise missed as a novice.

Of course, there are exceptions to this general rule, such as when you require multiple statements on a single line where semicolons are required as statement separators.

<b> End of indentation is end of block </b>
<br>

The last syntax difference covered in this post is similar to the previous one. Blocks of codes in C++ are not indentation sensitive or explicitly required. In Python however, consistent indentation of all statements in a given nested block <b> the same distance </b> to the right is necessary such that Python can determine where the block starts and stops. This is a huge win for code readability and a good habit that i would commit to when programming in C++ as well.
