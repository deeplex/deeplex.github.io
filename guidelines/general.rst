
=======================
 General
=======================

--------------------------
 *Cookiecutter* templates
--------------------------

For projects different *Cookiecutter* templates are provided.
Usage is mandatory.
If your project has no fitting template, please issue it `here <TODO>`_.
Existing templates are:

* C++

Refer to the respective coding guidelines for further information regarding your project.

---------------
 Documentation
---------------

Documentation is mandatory and missing documentation embarassing.
The layout for documentation is provided by our *Cookiecutter* documentation template.
It is automatically included by all other templates.
The respective content is created in `docs`.

If the documentation template is not created, please submit an issue in our `Cookiecutter repository <https://TODO.com>`.
You can generate the *Cookiecutter* template using the *Cookiecutter* script.

.. warning:: If the documentation is created using the *Cookiecutter* script, the `domain <https://www.sphinx-doc.org/en/master/usage/restructuredtext/domains.html>`_ is not set.

Documentation is generated using `sphinx <https://www.sphinx-doc.org/>`_.
The `requirements.txt` to install the required packages is provided with the *Cookiecutter* template for documentation and therefore in the `docs` folder of your project.

Then run (in your project root)
::

    sphinx-build ./docs /docs/build

To create the documentation.
Your documentation is generated as `./docs/build/index.html` respectively.

When using more than one programming language in your project, please update the `conf.py` to include the respective `domain <https://www.sphinx-doc.org/en/master/usage/restructuredtext/domains.html>`_.

-----------------
 Version control
-----------------

TODO: Git commits
