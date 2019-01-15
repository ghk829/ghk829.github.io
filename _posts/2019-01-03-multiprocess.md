---
layout: post
title:  "Multiprocess Context 유지"
date:   2019-01-03
excerpt: "Python Multiprocess"
tag:
- python
- Flask
- Spring boot
comments: false
---
# Multi-process in python Part 1 : *Handling a process with multiprocessing module*

* When it comes to using Multiprocessing.
* There're a lot of blog or stackoverflow for guide

* Link : [Multiprocess-basic](https://pymotw.com/2/multiprocessing/basics.html)


 But, It's complicated to manage multi-process

### Result & Stop the Process

I've developed a big-data platform.
If i run a process for running a component ex) Machine Learning Algorithms

It takes lots of time. So I should implement a interface for handling the process.


``` python
# proc is a process & out_q is a queue for receiving the process's result
if proc.is_alive():
      result = out_q.get()

```


The process takes lots of time.
So, beginner would code like the above.
Because, The API caller doesn't know how much time it takes and if the queue has a time-out then the process can be quited even though the process hasn't received the result yet.

But, In Python, It's very dangerous when it comes to stopping the Process if programmers want to manage the process.

If API caller requests a thread for stopping the running process.
the code could like below :



``` python


```

Even though the thread release all the source in queue of the running process,
the queue doesn't stop because the thread of the running process waits for the queue would get the result of the process.

So, I think the below code can solve this problem  :


``` python


```

Because the thread of the running process always check the queue has a result,
if the queue release all the source, then the queue can be quit by the thread which is called to stop the process.
