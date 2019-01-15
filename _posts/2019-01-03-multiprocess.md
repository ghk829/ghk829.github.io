---
layout: post
title:  "Multiprocess Context 유지"
date:   2019-01-03
excerpt: "Python Multiprocess"
project: true
tag:
- python
- Flask
- Spring boot
comments: false
---

* When it comes to using Multiprocessing.
* There're a lot of blog or stackoverflow for guide

Link : [Multiprocess-basic](https://pymotw.com/2/multiprocessing/basics.html)


 But, It's complicated to manage multi-process

### Result & Stop the Process

I've developed a big-data platform.
If i run a process for running a component ex) Machine Learning Algorithms
It takes lots of time.
So I should implement a interface for handling the process.


``` python
# proc is a process & out_q is a queue for receiving the process's result
if proc.is_alive():
      result = out_q.get()

```


The process takes lots of time.
So, beginner would code like the above.
Because, The API caller doesn't know how much time it takes.

But, In Python, It's very dangerous when it comes to stopping the Process
