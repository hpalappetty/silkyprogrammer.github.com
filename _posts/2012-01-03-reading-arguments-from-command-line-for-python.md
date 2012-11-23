---
layout: post
title: 'Reading arguments from Command line in python 3+'

---

I was in a situation where I had to read 2 arguments from python command line.

so the situation would look like this in IDLE.

&gt;&gt;  31 123.00 ( please note there is a space between 31 and 123.00)

The easiest way I felt, I could solve it is as follows:

#!usr/bin/env python
#withdrawl.py
list = input().split(' ',1)  #comments below
amt=float(list[0])
bal=float(list[1])

#comments

#the input() method reads the argument, split() method splits the string and move it to a list as follows ['31','123.00'], which we can read easily as list[0] and list[1].

once we get these details out, we can process it as we like.

#end of comments
