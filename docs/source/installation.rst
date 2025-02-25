Installation
============

.. _installation:

Frontend Installation
---------------------
:Latest:

You can install the latest release of SocDrawer through the `App store <https://google.com>`_ or `Google Play <https://google.com>`_.

:Staging:

You can download the latest Staging release from our `GitHub repository <https://github.com/5C-UoP/soc-drawer>`_ for all supported platforms. For Debian based linux distrubtions, macOS and windows systems, you just need to open the app by double clicking it. Other linux distributions don't guarentee compatibility but should work through wine OR preferably by extracting the .tar.gz and running the bin/SocDrawer executable.

:Development:

To install the development version you need to make sure you have the following dependencies installed.

- Git
- Flutter ^3.5.4

  - Android Studio
  - VS Code
  - Xcode (For MacOS / iOS deployment)
  - Android SDK
- Dart

First clone the repository and enter it with the following command

.. code-block:: console

    $ git clone git@github.com:5C-UoP/soc-drawer.git
    $ cd soc-drawer/

Then install dependencies

.. code-block:: console

    $ flutter pub get

And finally run the project

.. code-block:: console

     $ flutter run

.. FIXME: Can we self-document flutter code like we can sphinx? If so, include a link to the api reference here

Backend Installation
--------------------
:Dependencies:

For the latest release, please ensure you have the `Docker Engine <https://docs.docker.com/engine/install/>`_ installed, as it will manage your database installation for you. For all other releases you need:

- Python
- Pip
- MySQL


:Latest:

The backend is automatically pulled to the server from the GitHub container registry using `watchtower <https://containrrr.dev/watchtower>`_ You can specify a version by pulling the container of that specific version and deleting watchtower from the compose.prod.yaml file or by running the compose.yaml file, which doesn't include watchtower or a reverse proxy.

:Staging:

You can download staging builds from the `Release Page <https://github.com/5C-UoP/soc-drawer-backend>`_. To run, navigate to the download and install dependencies with

.. code-block:: console

     $ pip install -r requirements.txt

Then run the project using

.. code-block:: console

     $ python app.py

:Development:

First clone the repository and enter it with the following command

.. code-block:: console

    $ git clone git@github.com:5C-UoP/soc-drawer-backend.git
    $ cd soc-drawer-backend/

Then install dependencies

.. code-block:: console

    $ pip install -r requirements.txt

And finally run the project

.. code-block:: console

     $ python app.py

Please see the :ref:`API` documentation for information about developing SocDrawer.


Running Tests
-------------

Tests are ran on each commit to every branch, and every merge commit. In order to merge a branch, the tests must pass. Tests should be developed for every new feature you have made. Backend tests are located in the /tests folder. To run the backend tests, simply type the following from the root directory in your backend folder.

.. code-block:: console

     $ pytest

.. FIXME: Frontend tests?