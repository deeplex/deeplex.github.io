====
 C#
====

C# is to be created using respective Visual Studio Project templates.
Usage of a strict pattern like *MVVM* or *MVC*.
The respective usage is to be documented in the project you are using.

Every class should be put into a separate file.
This ensures assignability when creating `tests <Testing_>`_
Feel free to add directories for a more concise structure of your project.

---------------
 Documentation
---------------

Since projects are not created using `copier` templates the documentation has to be added using the `copier-documentation <../copier-documentation>`_ template.

Inline documentation can be added using `sphinx-autoapi <https://sphinx-autoapi.readthedocs.io/en/latest/tutorials.html#net>`_.

.. TODO

---------
 Testing
---------

Testing is mandatory and has to be included in every commit.
For *C#* `xUnit <https://xunit.net/>`_ is to be used.
It is recommended to you `this extension <https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator>`_ to be able to easily add tests to your project.


.. image:: /_static/images/visual_studio_create_unit_tests_context_menu.png
    :align: left
    :width: 40 %

.. image:: /_static/images/visual_studio_create_unit_tests.png
    :align: right
    :width: 50 %


The settings in :code:`Create Unit Tests` should not be changed.
If a test project already exists for your respective code you should select it.

For better readability of your tests use `FluentAssertions <https://github.com/fluentassertions/fluentassertions>`_.

Mocks are created using `FakeItEasy <https://github.com/FakeItEasy/FakeItEasy>`_.

Code coverage can not be checked using the Visual Studio Community edition, as this feature is only enabled for the `Visual Studio Enterprise <https://docs.microsoft.com/en-us/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested?view=vs-2022>`_ edition.

.. TODO Maybe code coverage can be checked using github actions?
