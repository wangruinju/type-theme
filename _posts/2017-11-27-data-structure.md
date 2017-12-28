---
layout: post
title: Data Structure (Draft)
tags: [data-science, leetcode]
---

Before I decided to make data science as my career goal, I was Physics PhD who did a lot of tool operations and optical measurements. Coding is not a daily work for me. I want to introduce a little bit about my background and encourage people who have the same backgroud like me or is a new learner in data structure. Before learning data structure, I have known some basic knowlege about Matlab and C. I used Matlab to visualize 2D electronic signal in my daily PhD life. When I was freshman at Nanjing University, I had a really bad experience of learning C langurange and wasted a lot of time debuging the synatax. Anyway, I was new to data structure before 2017 spring. 

Therefore, there is no hard thing until you enter that comfortable zone. The following is my learning experience of data structure. Still thanks to Zhijun Yin and Lingjun Fu, I learn a lot from them about where to start learning Python. Python has gained great attention in the data science field since 2016 and have a trend over R recently. For people who want to learn some resources about R, I will update it in other blogs.

# Online Courses

There are many online resources in MOOC and open courses. 

* [Google 3-Day Python](https://developers.google.com/edu/python/)

**Estimated time: 6 hours**

The first I would recommend is the Google Python education. It allows you to get familar with Python in a few class and have some hands-on experience. Here you will learn basic knowledge about string, list, set, dict and some re expressions. The homework is also great to give a try. 

* [Learn Python the Hard Way](https://learnpythonthehardway.org/)

**Estimated time: unknown**

Another great resourse is learn Python the hard way. I learn about how to print your results using Python. If you are familar with this part, you can skip it.

* [MIT Introduction to Algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-spring-2008/)

>[Youtube Videos](https://www.youtube.com/playlist?list=PLUl4u3cNGP61Oq3tWYp6V_F-5jb5L2iHb)

**Estimated time: one month**

I personally dive deep into the algorithm from this amazing course. Many thanks to MIT open courses. In this course, the lecturers wrote everything on the blackboard, allowing you to **taking notes** while listening. You can skip some parts if you feel like that you will never use them. You can take the following Leetcode topics as reference.

A good tip to learn some data struture is to follow some simple cases and write results in each loop or opreation on the while/black board or draft papers. After you understand the simple case many times, you will naturally get what is the essence of this algorithm. Also, please feel free to search any short video in Youtube. The following link is my favorite lecturer in India, who gave a very good explaination of each data structure.

>[Lectures by Ravindrababu Ravula](https://www.youtube.com/watch?v=aGjL7YXI31Q&list=PLEbnTDJUr_IeHYw_sfBOJ6gk5pie0yP-0)

* [Problem Solving with Algorithms and Data Structures using Python](http://interactivepython.org/runestone/static/pythonds/index.html)

**Estimated time: one month**

This is a fatastic book about Python data structure. I highly recommended for programming beginners. I would like to repeat the codes in the book and have a better understanding of each algorithm like sorting in the array or various transverse methods in the tree.

# [Leetcode](leetcode.com)

LeetCode is a platform for preparing technical coding interviews. The following is my suggestions of each topics.

I first get started with linked list suggested by my friend. It was not that difficult. There are some summary or tricks about linked list:

>[Linked list summary](http://www.cnblogs.com/Raising-Sun/p/5970662.html#3534606)

Then followed by binary search and two pointers. And some summary about bit manipulation can be looked up:

>[Bit manipulation summary](https://www.hackerearth.com/practice/notes/bit-manipulation/)

Then maybe math problems. If it is related with number theory, I guess you can skip or look at the solutions instead. Stack or hash table for some questions are not hard. However, combining with backtrack, tree, dfs, bfs or dp together, the solutions become more complicated. String and array questions are sort of solved in various methods. You can test yourself after you undestand all the algorithms. DP can be really hard.

Attach is my solutions:

**Linked List**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Linked%20List/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Linked%20List/medium.md)

**Binary Search**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Binary%20Search/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Binary%20Search/medium.md)

**Two Pointers**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Two%20Pointers/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Two%20Pointers/medium.md)

**Bit Manipulation**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Bit%20Manipulation/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Bit%20Manipulation/medium.md)

**Math**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Math/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Math/medium.md)

**Stack**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Stack/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Stack/medium.md)

**Hash Table**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Hash%20Table/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Hash%20Table/medium.md)

**Backtrack**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Backtrack/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Backtrack/medium.md)

**Tree**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Tree/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Tree/medium.md)

**DFS**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/DFS/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/DFS/medium.md)

**BFS**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/BFS/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/BFS/medium.md)

**String**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/String/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/String/medium.md)

**Array**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Array/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Array/medium.md)

**Dynamic Programming**

>[easy](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Dynamic%20Programming/easy.md)

>[medium](https://github.com/wangruinju/Rui_Python_Leetcode/blob/master/Dynamic%20Programming/medium.md)