.. _obiettivo_1:

Target 1: going back in time
############################

So, if in git everything is stored in a key/value database, there will
probably be a way to reference any object in the database using its key.

And in fact there is.

Now let's try to go back in time, to ``commit A``, using the ``git 
checkout`` command.

The ``checkout`` command takes the indicated ``commit`` and copies it
to ``file system`` and to ``staging area``.

.. figure:: img/index-add-commit-checkout.png

Ok: but what is ``commit A``'s key? You can discover it with a graphical
client or with the ``git log`` command, that shows a list of all ``commits`` 
stored in ``repository``

.. code-block:: bash

    git log --oneline
    2a17c43 Commit B, My second commit
    56674fb commit A, My first commit

Be careful! Since ``commit`` memorizes also date and author, your keys
will result different than mine. On my ``repository`` ``commit A``'s key is
``56674fb``. 

Ok: let's go back to the past, to the moment of ``commit`` ``A``

.. code-block:: bash

    ls
    doh.html    libs    templates
    
    git checkout 56674fb
    
    ls
    libs    templates

In effect, except for a mysterious and long-winded message where git complains for being
in ``'detached HEAD' state`` (afterwards we'll make this point clearer), file system has 
returned to the state of first commit, and in fact, file ``doh.html`` disappeared.

If you try to run `gitk` again , you'll receive another surprise: apparently `commit B` 
disappeared. But don't worry: git is just hiding it. In order to visualize all
commits, use the `--all` option of `gitk`

.. code-block:: bash
                
    gitk --all

This happens because, usually, git's graphic interfaces try to show only meaningful 
commits, hiding every unnecessary element. 
Gitk, for instance, shows only commits belonging to the development line that gets 
to current position, omitting what follows in the development line (that is its
future) and any other branches. 
In the case of our history, from the viewpoint of `commit A`, `commit B` belongs to
the future, and unless we ask explicitly to show it, it'll be omitted in the 
visualization 

Below, whenever you should be amazed because you've the impression that git made some 
``commit`` disappear, rest assured typing 

.. code-block:: bash
                
    gitk --all

or

.. code-block:: bash
                
    git log --graph --all --oneline

if you prefer not to abandon the shell.
:ref:`Indice <indice>` :: :ref:`Obiettivo 2: divergere <obiettivo_2>`
