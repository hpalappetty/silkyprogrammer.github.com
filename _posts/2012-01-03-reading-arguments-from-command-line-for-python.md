---
layout: post
title: 'Reading arguments from Command line in python 3+'

---
<p>
I was in a situation where I had to read 2 arguments from python command line.
 So the situation would look like this in IDLE.</p>

    >>>31 123.00 ( please note there is a space between 31 and 123.00)

The easiest way I felt, I could solve it is as follows:

      #!usr/bin/env python
      #withdrawl.py
      list = input().split(' ',1)  #comments below
      amt=float(list[0])
      bal=float(list[1])

<p>
The input() method reads arguments, split() method splits the
string(argv) and move it to a list as follows ['31','123.00'], which we can read easily as list[0] and list[1].
Once we get the data out, we can process it as we like.</p>
