CCM
---

Configuration Cache Manager
~~~~~~~~~~~~~~~~~~~~~~~~~~~

These modules handle the conversion of an XML or JSON profile into a local binary cache, and give the API for Quattor modules to access these caches.

If you are writing a Quattor-client module, all you probably need is the getElement and getTree methods from a Configuration object. Typically you will combine them like this:

```my $tree = $cfg->getElement("/foo/bar")->getTree();```

And you will have a reference to a data structure, identical to what you defined in your profile.

For more information, see the man pages.

.. toctree::
    :caption: CCM
    :maxdepth: 1
    :glob:

    CCM/*
