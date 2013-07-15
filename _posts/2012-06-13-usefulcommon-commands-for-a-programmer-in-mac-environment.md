---
layout: post
title: 'Useful/Common commands for a Programmer in { Mac environment }'

---
<p>
At home , I keep fiddling with my computer  installing open source code base to read through and learn about the way different people write code. During these sessions, I noticed that, a specific set of commands were used on a daily basis to get my work done on terminal and I felt that it might be useful  for the people with bad memory ( especially me ;)). A useful excuse to write few lines ;) . Here is the list of frequently used commands by me while working on pet projects.</p>
<p>
{<em>PS: This list and the descrption of all the commands will get updated as and when I get more time.Please note this is not a final list, it's an ever growing one ;)}</em>
</p>
<p>
<strong>Mac Terminal:</strong>
</p>
$ cd [<em>directory - name]</em>
<p>
This command helps the user to change the directory/navigate up/down through the directories.
</p>
$ mkdir [<em>new- directory - name]</em>
<p>
This command helps the user to make/create a new directory.
</p>
$ ls -ltr
<p>
This command helps the user to list all the files and directories recursively except the hidden one.
</p>

$ ls -la
<p>
This command  helps the user to list all the files/directories including the hidden ones with a "." in the name [e.g. ".profile"]</p>
$ ls -l | egrep `^d'
<p>
This command helps the user to list all the directories.
</p>
$ nano .profile  [<em>I use nano, instead of "vi", please use an editor of your choice]</em>
<p>
This is to change .profile file to set the PATH. You can find the .profile file in the home directory. use ctrl +O to save the file and ctrl+x to exit from the file. After you complete this step you have to run/execute this .profile file once to get the set PATH up and working for you. TO DO THAT type in   $  .  ./.profile  and press enter.
</p>
$ echo $PATH
<p>
This will show you all the set values in system PATH. This is similar to the stuff , we see in Windows PATH variable .
</p>
$ sudo ln -s [path-1]/something  /usr/local/bin/[something]
<p>
e.g. sudo ln -s /path/to/django/bin/django-admin.py /usr/local/bin/django-admin.py
</p>