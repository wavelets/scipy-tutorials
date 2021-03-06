Basic types
============

Numbers
--------

* IPython as a calculator:

  .. sourcecode:: ipython

    In [1]: 1 + 1
    Out[1]: 2

    In [2]: 2**10
    Out[2]: 1024

    In [3]: (1 + 1j)*(1 - 1j)
    Out[3]: (2+0j)

* scalar types: int, float, complex

  .. sourcecode:: ipython

    In [4]: type(1)
    Out[4]: <type 'int'>

    In [5]: type(1.)
    Out[5]: <type 'float'>

    In [6]: type(1 + 0j)
    Out[6]: <type 'complex'>

.. warning:: Integer division

    .. sourcecode:: ipython

	In [7]: 3/2
	Out[7]: 1

	In [8]: from __future__ import division

	In [9]: 3/2
	Out[9]: 1.5

    **Trick:** Use floats

    .. sourcecode:: ipython

	In [10]: 3./2
	Out[10]: 1.5

* Type conversion:

  .. sourcecode:: ipython

    In [11]: float(1)
    Out[11]: 1.

.. topic:: Exercise:

    Compare two approximations of pi: 22/7 and 355/113

    (pi = 3.14159265...)

Collections
------------

Collections: list, dictionaries (and strings, tuples, sets, ...)

Lists
~~~~~~

.. sourcecode:: ipython

    In [12]: l = [1, 2, 3, 4, 5]

* Indexing:

  .. sourcecode:: ipython

    In [13]: l[2]
    Out[13]: 3

  Counting from the end:

  .. sourcecode:: ipython

    In [14]: l[-1]
    Out[14]: 5

* Slicing:

  .. sourcecode:: ipython

    In [15]: l[3:]
    Out[15]: [4, 5]

    In [16]: l[:3]
    Out[16]: [1, 2, 3]

    In [17]: l[::2]
    Out[17]: [1, 3, 5]

    In [18]: l[-3:]
    Out[18]: [3, 4, 5]

  **Syntax:** `start:stop:stride`

* Operations on lists:

  Reverse `l`:

  .. sourcecode:: ipython

    In [19]: r = l[::-1]

    In [20]: r
    Out[20]: [5, 4, 3, 2, 1]

  Append an item to `r`:

  .. sourcecode:: ipython

    In [21]: r.append(3.5)

    In [22]: r
    Out[22]: [5, 4, 3, 2, 1, 3.5]

  Extend a list with another list (in-place):

  .. sourcecode:: ipython

    In [23]: l.extend([6, 7])

    In [24]: l
    Out[24]: [1, 2, 3, 4, 5, 6, 7]

  Concatenate two lists:

  .. sourcecode:: ipython

    In [25]: r + l
    Out[25]: [5, 4, 3, 2, 1, 3.5, 1, 2, 3, 4, 5, 6, 7]
 

  Sort `r`:

  .. sourcecode:: ipython

    In [26]: r.sort()

    In [27]: r
    Out[27]: [1, 2, 3, 3.5, 4, 5]

.. note:: **Methods:**
    
    `r.sort`: `sort` is a method of `r`: a special function to is applied
    to `r`.

.. warning:: **Mutables:**
    
    Lists are mutable types: `r.sort` modifies in place `r`.

.. note:: **Discovering methods:**

    In IPython: tab-completion (press tab)

    .. sourcecode:: ipython

	In [28]: r.
	r.__add__           r.__iadd__          r.__setattr__
	r.__class__         r.__imul__          r.__setitem__
	r.__contains__      r.__init__          r.__setslice__
	r.__delattr__       r.__iter__          r.__sizeof__
	r.__delitem__       r.__le__            r.__str__
	r.__delslice__      r.__len__           r.__subclasshook__
	r.__doc__           r.__lt__            r.append
	r.__eq__            r.__mul__           r.count
	r.__format__        r.__ne__            r.extend
	r.__ge__            r.__new__           r.index
	r.__getattribute__  r.__reduce__        r.insert
	r.__getitem__       r.__reduce_ex__     r.pop
	r.__getslice__      r.__repr__          r.remove
	r.__gt__            r.__reversed__      r.reverse
	r.__hash__          r.__rmul__          r.sort


Dictionaries
~~~~~~~~~~~~

Dictionaries are a mapping between keys and values:

  .. sourcecode:: ipython

    In [29]: d = {'a': 1, 'b':1.2, 'c':1j}

    In [30]: d['b']
    Out[30]: 1.2

    In [31]: d['d'] = 'd'

    In [32]: d
    Out[32]: {'a': 1, 'b': 1.2, 'c': 1j, 'd': 'd'}

    In [33]: d.keys()
    Out[33]: ['a', 'c', 'b', 'd']

    In [34]: d.values()
    Out[34]: [1, 1j, 1.2, 'd']

.. warning:: Keys are not ordered

.. note:: Dictionnaries are an essential data structure

    For instance to store precomputed values.

Strings
~~~~~~~~

* Different string syntaxes::

    a = 'Mine'
    a = "Chris's"
    a = '''Mine
	   and not his'''
    a = """Mine
	   and Chris's"""

* Strings are collections too:

  .. sourcecode:: ipython

    In [35]: s = 'Python is cool'

    In [36]: s[-4:]
    Out[36]: 'cool'

* And they have many useful methods:

  .. sourcecode:: ipython

    In [37]: s.replace('cool', 'powerful')
    Out[37]: 'Python is powerful'

.. warning:: Strings are not mutable

* String substitution:

  .. sourcecode:: ipython

    In [38]: 'An integer: %i; a float: %f; another string: %s' % (1, 0.1, 'string')
    Out[38]: 'An integer: 1; a float: 0.100000; another string: string'


More collection types
~~~~~~~~~~~~~~~~~~~~~

* **Sets:** non ordered, unique items:

  .. sourcecode:: ipython

    In [39]: s = set(('a', 'b', 'c', 'a'))

    In [40]: s
    Out[40]: set(['a', 'b', 'c'])

    In [41]: s.difference(('a', 'b'))
    Out[41]: set(['c'])

  Sets cannot be indexed:

  .. sourcecode:: ipython

    In [42]: s[1]
    ---------------------------------------------------------------------------
    TypeError                                 Traceback (most recent call last)

    TypeError: 'set' object does not support indexing


* **Tuples:** non-mutable lists:

  .. sourcecode:: ipython

    In [43]: t = 1, 2
    
    In [44]: t
    Out[44]: (1, 2)
    
    In [45]: t[1]
    Out[45]: 2
    
    In [46]: t[1] = 2
    ---------------------------------------------------------------------------
    TypeError                                 Traceback (most recent call last)
    
    TypeError: 'tuple' object does not support item assignment
    

