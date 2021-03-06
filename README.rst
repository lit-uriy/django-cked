Django CKEd
===========

|PyPI version| |Downloads| |Python versions| |Development Status| |License|

**CKEditor and elFinder integration for Django Framework.**

Provides a ``RichTextField`` and ``CKEditorWidget`` with upload and
browse support.

|CKEditor| |elFinder|

Installation
------------

::

    pip install django-cked

or

::

    pip install -e hg+https://bitbucket.org/CWTeam/django-cked#egg=django-cked

Configuration
-------------

Add ``cked`` to your ``INSTALLED_APPS`` setting.

Then set ``ELFINDER_OPTIONS`` in your settings:

::

    ELFINDER_OPTIONS = {
        ## required options
        'root': os.path.join(PROJECT_ROOT, 'media', 'uploads'),
        'URL': '/media/uploads/',
    }

And add CKEd URL include to your project ``urls.py`` file:

::

    url(r'^cked/', include('cked.urls')),

Settings
--------

-  **CKEDITOR\_OPTIONS**: CKEditor config. See
   http://docs.ckeditor.com/#!/guide/dev_configuration
-  **ELFINDER\_OPTIONS**: elFinder config. See
   https://github.com/Studio-42/elFinder/wiki/Client-configuration-options

Usage
-----

Model field
~~~~~~~~~~~

::

    from django.db import models
    from cked.fields import RichTextField


    class Entry(models.Model):
        text = RichTextField()

Widget
~~~~~~

::

    from django import forms
    from cked.widgets import CKEditorWidget

    class MyForm(forms.Form):
        text = forms.CharField(widget=CKEditorWidget)

**NOTE**: If you are using custom forms, dont’r forget to include form
media to your template:

::

    {{ form.media }}

.. |CKEditor| image:: https://bitbucket.org/CWTeam/django-cked/raw/default/img/ckeditor.jpg
.. |elFinder| image:: https://bitbucket.org/CWTeam/django-cked/raw/default/img/elfinder.jpg

.. |PyPI version| image:: https://pypip.in/version/django-cked/badge.svg
    :target: https://pypi.python.org/pypi/django-cked/
    :alt: Latest Version

.. |Downloads| image:: https://pypip.in/download/django-cked/badge.svg
    :target: https://pypi.python.org/pypi//django-cked/
    :alt: Downloads

.. |Python versions| image:: https://pypip.in/py_versions/django-cked/badge.svg
    :target: https://pypi.python.org/pypi/django-cked/
    :alt: Supported Python versions

.. |Development Status| image:: https://pypip.in/status/django-cked/badge.svg
    :target: https://pypi.python.org/pypi/django-cked/
    :alt: Development Status

.. |License| image:: https://pypip.in/license/django-cked/badge.svg
    :target: https://pypi.python.org/pypi/django-cked/
    :alt: License