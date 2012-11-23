---
layout: post
title: 'Django Managers'

---

A manager is a special attribute used to query the Database while using Django framework.

For e.g. In Django code  <strong>Person.objects.all</strong>

=&gt; <strong>Person</strong> is the <strong>model</strong>.
=&gt; <strong>objects</strong> is the <em><strong>manager</strong></em><strong></strong>.
<strong>Points to remember:</strong>
<ol>
	<li>Each Django model has at least one manager.</li>
	<li>It is possible to write custom managers.</li>
</ol>
Why do we need custom manager? There are several reasons , but the most common ones being,
<ol>
	<li>To add extra manager methods to provide table-level functionality to models.</li>
	<li>To modify the initial QuerySet that is returned by the manager.</li>
	<li>Helps to avoid having duplicate code.</li>
</ol>
<strong>Example of a custom manager for Person Model</strong>

#models.py
from django.db import models

<em>class PersonManager(models.Manager):</em>
<em> def person_count(self,keyword):</em>
<em> return self.filter(name__icontains = keyword).count()</em>

<em>class Person(models.Model):</em>
<em> name = models.CharField(max_length=50)</em>
# some code goes here ...
<em>objects = PersonManager()</em> # This assignment will replace the "default" manager for the model.

<em>&gt;&gt;&gt; Person.objects.person_count('john')</em> # will return the count of people with name 'John'
3

You can modify initial QuerySet by overriding Manager.get_query_set() method. A good example is

<em>class MaleManager(models.Manager):</em>
<em> def get_query_set(self):</em>
<em> return super(MaleManager, self).get_query_set().filter(sex='M') # filter Male.</em>

<em>class FemaleManager(models.Manager):</em>
<em> def get_query_set(self):</em>
<em> return super(FemaleManager, self).get_query_set().filter(sex='F') # filter Female's</em>

<em>class Person(models.Model):</em>
<em> first_name = models.CharField(max_length=50)</em>
<em> last_name = models.CharField(max_length=50)</em>
<em> sex = models.CharField(max_length=1, choices=(('M', 'Male'), ('F', 'Female')))</em>
<em>people = models.Manager()</em> # default manager
<em>malemgr = MaleManager()</em> # manager to manipulate initial query set for filtering males.
<em>femmgr = FemaleManager()</em> # manager to manipulate initial query set for filtering females.

Calls to these managers are done as follows:
<em>&gt;&gt;&gt; Person.malemgr.all()</em>
<em> &gt;&gt;&gt; Person.femmgr.all()</em>
<em> &gt;&gt;&gt; Person.people.all()</em>
