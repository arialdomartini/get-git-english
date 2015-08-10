.. _obiettivo_2:

Target 2: diverging
###################

Using a graphic convention that is very common in git's literature, we 
could represent the present situation in your repository with 

    **A**---B

That is: there are two ``commit`` , ``A`` and ``B``. ``commit B`` is
``A``'s son (time moves to the right). The bolded ``commit`` identifies 
the point where you presently are.

What would happen if I now made some changes and than committed?
It would happen that the new ``commit C`` that would be generated will
be ``A``'s son (because you're starting from there), but the development
line would go on diverging from the ``A---B`` line.

That is,it would create this situation

.. code-block:: bash

    A---B
     \
      C     
Test:

.. code-block:: bash

    echo "ei fu siccome immobile" > README.md
    git add README.md 
    git commit -m "Here you have the C commit"

Show the result with

.. code-block:: bash

    gitk --all


.. figure:: img/repo1.png

You got a branch, without the mechanism of file copy used by SVN at
the moment of creation of a branch: git's model based on key/value and 
pointers makes it very economic to represent a diverging development line.

Two important observations.

The first in order to reiterate the concept that never git memorized deltas between
files:  ``A``, ``B`` and ``C`` are snapshots of the whole project. It's 
very important to remember this, because it'll help you in understanding
that all observations you've always been in the habit of making with SVN
might not apply with SVN.

The second might surprise you a little: the two diverging development lines you
have just seen are not ``branch``. In git a ``branch`` is a pointer with a name,
or a label. I'm going to speak about this in next paragraph, but get accustomed to
the idea that in git ``branch`` are not development branches.

:ref:`Indice <indice>` :: :ref:`Obiettivo 3: creare un branch <obiettivo_3>`
