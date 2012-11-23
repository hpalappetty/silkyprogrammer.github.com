---
layout: post
title: 'Django Custom Template Filters'

---

Django custom templates are nothing but our good old python functions with one or two arguments.  e.g. {{request |session:"mark"}} , the filter  "<em>session"</em>  will be substituted t with the variable <em>"request" .</em>The catch is these functions should always fail silently and should return something(preferably something meaningful).

# A function that brings food for me.
def  bringMeFood(val, arg):
""" Gets me all the food I need."""
return val.getMeFood(arg,' ')

# A function that gets me water.
def fetchWater(val):
"""Goes and gets water"""
return val.getMeWater()

After writing the filter definition we got to register our filters with the Library instance to make it available for Django ecosystem (template language to be precise here). This is done by calling the <strong>Library.filter('filter name', 'filter function')</strong>.

@register.filter(name='fetchwater')
def fetchWater(val):
"""Goes and gets water"""
return val.getMeWater()

@register.filter
def fetchWater(val):
"""Goes and gets water"""
return val.getMeWater()

- * Observe if we leave out the name, Django will use function's name as Filter Name.
