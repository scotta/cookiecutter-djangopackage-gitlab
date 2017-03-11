======================================
Cookiecutter Django Package for GitLab
======================================

.. image:: https://travis-ci.org/pydanny/cookiecutter-djangopackage-gitlab.svg?branch=master
    :target: https://travis-ci.org/pydanny/cookiecutter-djangopackage-gitlab

A cookiecutter_ template for creating reusable Django packages (installable apps) quickly.

This is a detached fork of `cookiecutter-djangopackage`_ (4cf583b) using GitLab

**Why?** Creating reusable Django packages has always been annoying. There are no defined/maintained
best practices (especially for ``setup.py``), so you end up cutting and pasting hacky, poorly understood,
often legacy code from one project to the other. This template, inspired by `cookiecutter-pypackage`_,
is designed to allow Django developers the ability to break free from cargo-cult configuration and follow
a common pattern dictated by the experts and maintained here.

.. _Cookiecutter: https://github.com/audreyr/cookiecutter
.. _cookiecutter-pypackage: https://github.com/audreyr/cookiecutter-pypackage
.. _cookiecutter-djangopackage: https://github.com/pydanny/cookiecutter-djangopackage

Features
--------

* Sane setup.py for easy PyPI registration/distribution
* Travis-CI configuration
* Codecov configuration
* Tox configuration
* Sphinx Documentation
* BSD licensed by default
* Basic model generation (optional)
* Structured to use GitLab

Usage
-----

First, create your empty repo on GitLab (in our example below, we would call it ``blogging_for_humans``) and set up your
 virtual environment with your favorite method.

**Note**: Your project will be created with README.rst file containing a pypi badge, a travis-ci badge and a link to
 documentation on readthedocs.io. You don't need to have these accounts set up before using Cookiecutter or
 cookiecutter-djangopackage.

Now, get Cookiecutter_::

    $ pip install cookiecutter

Now run it against this repo::

    $ cookiecutter https://github.com/scotta/cookiecutter-djangopackage-gitlab.git

You'll be prompted for some questions, answer them, then it will create a directory that is your new package.

Let's pretend you want to create a reusable Django app called "Blogging-for-Humans", with an app that can be placed
in ``INSTALLED_APPS`` as "blogging_for_humans". Rather than have to copy/paste from other people's projects and
then fight enthusiasm-destroying app layout issues like `setup.py` configuration and creating test
harnesses, you get Cookiecutter_ to do all the work.

It prompts you for information that it uses to create the app, with defaults in square brackets. Answer them::

    Cloning into 'cookiecutter-djangopackage'...
    remote: Counting objects: 49, done.
    remote: Compressing objects: 100% (33/33), done.
    remote: Total 49 (delta 6), reused 48 (delta 5)
    Unpacking objects: 100% (49/49), done.
    full_name [Your full name here]: Forename Surname
    email [you@example.com]: forename.surname@my-mail-domain.com
    gitlab_group [groupname]: gitlab-groupname
    gitlab_username [yourname]: gitlab-username
    project_name [dj-package]: Blogging-for-Humans
    repo_name [blogging_for_humans]:
    app_name [blogging_for_humans]:
    project_short_description [Your project description goes here]: A sample Django package
    models [Comma-separated list of models]: Scoop, Flavor
    django_versions [1.8,1.9,1.10]:
    version [0.1.0]:
    create_example_project [N]:
    Select open_source_license:
    1 - MIT
    2 - BSD
    3 - ISCL
    4 - Apache Software License 2.0
    5 - Not open source
    Choose from 1, 2, 3, 4, 5 [1]:

Enter the project and take a look around::

    $ cd blogging_for_humans/
    $ ls

Create a GitLab repo and push it there::

    $ git init
    $ git add .
    $ git commit -m "first awesome commit"
    $ git remote add origin git@gitlab.com:gitlab-username/blogging_for_humans.git
    $ git push -u origin master

Now take a look at your repo. Awesome, right?

It's time to write the code!!!

Running Tests
~~~~~~~~~~~~~

Code has been written, but does it actually work? Let's find out!

::

    source <YOURVIRTUALENV>/bin/activate
    (myenv) $ pip install -r requirements_test.txt
    (myenv) $ python runtests.py

Setting up Travis
~~~~~~~~~~~~~~~~~

You will need to explicitly activate your repo in your `Travis CI profile`_.
If the repo isn't showing up, run a manual synchronisation.

.. _Travis CI profile: https://travis-ci.org/profile/

Integration with codecov.io
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Code coverage is integrated with `Codecov`_. Make sure you have an account
and that you've granted access to your repo. In case of a private repo, you
will need to generate a token and pass it when submitting coverage.

.. _CodeCov: https://codecov.io/

Register on PyPI
~~~~~~~~~~~~~~~~

Once you've got at least a prototype working and tests running, it's time to register the app on PyPI::

    python setup.py register


Releasing on PyPI
~~~~~~~~~~~~~~~~~

Time to release a new version? Easy!

First, use `bumpversion` to up the release number::

    $ pip install bumpversion
    $ bumpversion --current-version VERSION_NUMBER minor --config-file setup.cfg

Where `VERSION_NUMBER` is the current version, e.g. `0.1.0`.

Then run::

    $ python setup.py publish

It will answer with something like::

    You probably want to also tag the version now:
          git tag -a 0.1.0 -m 'version 0.1.0'
          git push --tags

Go ahead and follow those instructions.

Add to Django Packages
~~~~~~~~~~~~~~~~~~~~~~

Once you have a release, and assuming you have an account there,
just go to https://www.djangopackages.com/packages/add/ and add it there.

