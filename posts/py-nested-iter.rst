.. title: Python: nested iterator
.. slug: py-nested-iter
.. date: 2010-07-08 19:07:01
.. tags: python

Just a (probably) useful examle of nested Python generator written in
Python using recursive ***yield*** expression.


.. TEASER_END

.. code-block:: python

    #!/usr/bin/env python
    # -*- coding: utf-8 -*-

    sample = (1, 2, (3, 4, 5), 6, ((7, ), 8), 9)

    def cycle(smth):
        for i in smth:
            if isinstance(i, int):
                yield i**2
            else:
                for j in cycle(i):
                    yield j

    for j in cycle(sample):
        print(j)

    -------------

    1
    4
    9
    16
    25
    36
    49
    64
    81

