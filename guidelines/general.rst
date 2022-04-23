
=======================
 General
=======================

--------------------------
 *copier* templates
--------------------------

For projects different *copier* templates are provided.
Usage is mandatory.
For the installation of *copier*, refer to the `official documentation <./https://copier.readthedocs.io/en/latest/>`.

.. warning:: `pip install copier` will install *copier==5.1.0* as of now. Use `pip install copier==v6.0.0b0` instead.

Existing templates are:

* `C++ library <../copier-cpp-template>`_

Whether you want to create a new project using a template or want to issue a new template, refer to the coding guidelines for your respective language..

---------------
 Documentation
---------------

Documentation is mandatory and missing documentation embarassing.
The layout for documentation is provided by our *copier* documentation template.
It is automatically included by all other templates.
The respective content is created in `docs`.

.. warning:: If the documentation is created using the *copier* script, the `domain <https://www.sphinx-doc.org/en/master/usage/restructuredtext/domains.html>`_ is not set.

Documentation is generated using `sphinx <https://www.sphinx-doc.org/>`_.
The `requirements.txt` to install the required packages is provided with the *copier* template for documentation and therefore in the `docs` folder of your project.

Then run (in your project root)
::

    sphinx-build ./docs /docs/build

To create the documentation.
Your documentation is generated as `./docs/build/index.html` respectively.

When using more than one programming language in your project, please update the `conf.py` to include the respective `domain <https://www.sphinx-doc.org/en/master/usage/restructuredtext/domains.html>`_.

-----------------
 Version control
-----------------

`git <https://git-scm.com/>`_ has to be used for all projects.
The `master` (or `main`) branch has to pass all tests at all times.

To make changes first create an issue in the respective github repository.
Create a branch using the respective:
`Create a branch for this issue or link a pull request.` button.

.. image:: /_static/images/github_create_branch_from_issue.png
    :align: center

Prepend `dev/` for your branch name.
So for example a valid branch name is `dev/1_first_issue`.
For branches consisting of many issues create an epic issue.
Refer to GitHub templates for more information.

.. note:: GitHub templates are automatically generated using *copier* for your project.

Refer to the guidelines for tests for your respective language.

.. warning:: Every commit has to come with test coverage.

For *work in progress* commits first check out appending `-wip/<author_name>` to your branch name and do not forget to delete that *wip* branch as soon as it is no longer up to date.

Always follow `the seven rules of a great Git commit message <https://cbea.ms/git-commit/#seven-rules>`_:

* Separate subject from body with a blank line
* Limit the subject line to 50 characters
* Capitalize the subject line
* Do not end the subject line with a period
* Use the imperative mood in the subject line
* Wrap the body at 72 characters
* Use the body to explain what and why vs. how
