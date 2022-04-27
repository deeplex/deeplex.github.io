
==========
 Workflow
==========

The general workflow is shown in the following flowchart. It is meant as a general guideline.
If you want to differ in your project, please document the differences at the respective locations in your project documentation.

.. raw:: html
    :file: ../_static/workflow.html


----------------
 Create project
----------------

To create projects different *copier* templates are provided.
For the installation of *copier*, refer to the `official documentation <./https://copier.readthedocs.io/en/latest/>`.

.. warning:: `pip install copier` will install *copier==5.1.0* as of now. Use `pip install copier==v6.0.0b0` instead.

Existing templates are:

* `C++ library <../copier-cpp-template>`_
* `Documentation <../copier-documentation>`_

Whether you want to create a new project using a template or want to issue a new template, refer to the coding guidelines for your respective language.

.. note:: Sometimes it does not make sense to use one of our *copier* templates. Document your decision in the respective guidelines for the language and the documentation of the project itself.

Every project has to use the *copier-documentation* template for consistent understanding throughout all projects.
The *copier-documentation* template is provided with all other *copier* templates.
If you do not use one of the provided *copier* templates you have to install it in the root of your project.


--------------------
 Problem definition
--------------------

The *copier-documentation* templates also provides the project with issue templates.
At the moment there are two issue templates:
- Bug Report
- Feature Request

The templates provide the necessary guidelines to state the issue.
You can also create issues as a collection of other issues.

An issue state a clearly defined problem which can be solved with a series of commits.
It should also contain some idea how to solve the issue or kick of a discussion about that.


-----------------
 Version control
-----------------

`git <https://git-scm.com/>`_ has to be used for all projects.
The `master` (or `main`) branch has to pass all tests at all times.

To make changes first create an issue in the respective github repository.
Create a branch using the respective:
`Create a branch for this issue or link a pull request.` button.

.. .. image:: /_static/images/github_create_branch_from_issue.png
    .. :align: center

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


---------
 Testing
---------

It is recommended to define tests on the expected behavior.
Therefore if you implement the feature, or fixed a bug the test should be passed in the end.
Testing as a process differs from project to project.
Therefore it is likely that you have to define the respective process yourself.
Please provide respective documentation, so that others and future you can adhere to the same scheme.

.. note:: The coding guidelines for different languages define standards on how to test. If your project can not follow these, please document that and create an issue if your style should be implemented as well.


---------------
 Documentation
---------------

Documentation is mandatory and missing documentation embarassing.

*******
 Tools
*******

The layout for documentation is provided by our *copier-documentation* template.
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

********
 How-To
********

When it comes to how to document, please keep it short and simple.
When explaining how something works, or why something is done a specific way sticks to this pattern:

 - One sentence should contain exactly one thought.
 - One paragraph should contain exactly one idea.
 - One chapter should contain exactly one concept.

For flow charts or similar visual elements the usage of `diagrams.net <https://app.diagrams.net>`_ is recommended.

