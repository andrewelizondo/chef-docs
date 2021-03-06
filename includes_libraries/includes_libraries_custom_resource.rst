.. The contents of this file are included in multiple topics.
.. This file should not be changed in a way that hinders its ability to appear in multiple documentation sets.

.. This topic is NOT the same as the LWRP resource topic; keep separate.

A resource can also be defined in ``/libraries`` directory. Some advantages of this approach include more control over how resources behave in the provider, the ability to control the name of the resource directly, and more options available for writing tests. The resources and providers for a library resource, similar to lightweight resources (defined in the ``/resources`` and ``/providers`` folders) typically have a separate file for the resource and the provider, but this is not requirement. The main disadvantage of this approach is that resources defined in the ``/libraries`` directory may not use the |dsl recipe|.
