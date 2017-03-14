=============================
{{ cookiecutter.project_name }}
=============================

{% if cookiecutter.gitlab_groupname %}

.. image:: https://gitlab.com/{{ cookiecutter.gitlab_groupname}}/{{ cookiecutter.repo_name }}/badges/master/build.svg
    :target: https://gitlab.com/{{ cookiecutter.gitlab_groupname}}/{{ cookiecutter.repo_name }}/commits/master

.. image:: https://gitlab.com/{{ cookiecutter.gitlab_groupname}}/{{ cookiecutter.repo_name }}/badges/master/coverage.svg
    :target: https://gitlab.com/{{ cookiecutter.gitlab_groupname}}/{{ cookiecutter.repo_name }}/commits/master

{% else %}

.. image:: https://gitlab.com/{{ cookiecutter.gitlab_username }}/badges/master/build.svg
    :target: https://gitlab.com/{{ cookiecutter.gitlab_username }}/commits/master

.. image:: https://gitlab.com/{{ cookiecutter.gitlab_username }}/badges/master/coverage.svg
    :target: https://gitlab.com/{{ cookiecutter.gitlab_username}}/{{ cookiecutter.repo_name }}/commits/master

{% endif %}

{{ cookiecutter.project_short_description}}

The GitLab CI/CD Pipelines need to be configured to extract the code coverage statistics.
Please set the regular expression to :code:`TOTAL.*?(\d\d\%)`.

Quickstart
----------

Install {{ cookiecutter.project_name }}::

    pip install {{ cookiecutter.repo_name }}

Add it to your `INSTALLED_APPS`:

.. code-block:: python

    INSTALLED_APPS = (
        ...
        '{{ cookiecutter.app_name }}.apps.{{ cookiecutter.app_config_name }}',
        ...
    )

Add {{ cookiecutter.project_name }}'s URL patterns:

.. code-block:: python

    from {{ cookiecutter.app_name }} import urls as {{ cookiecutter.app_name }}_urls


    urlpatterns = [
        ...
        url(r'^', include({{ cookiecutter.app_name }}_urls)),
        ...
    ]

Features
--------

* TODO

Running Tests
-------------

Does the code actually work?

::

    source <YOURVIRTUALENV>/bin/activate
    (myenv) $ pip install tox
    (myenv) $ tox

Credits
-------

Tools used in rendering this package:

*  Cookiecutter_
*  `cookiecutter-djangopackage-gitlab`_

.. _Cookiecutter: https://github.com/audreyr/cookiecutter
.. _`cookiecutter-djangopackage-gitlab`: https://github.com/scotta/cookiecutter-djangopackage-gitlab
