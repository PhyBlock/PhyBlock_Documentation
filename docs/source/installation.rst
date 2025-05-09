Installation
============

.. _installation:

Frontend Installation
---------------------
:Latest:

You can install the latest release of SocDrawer through the `GitHub Releases Page <https://github.com/5C-UoP/soc-drawer/releases>`_.

:Staging:

You can download the latest Staging release from our `GitHub repository <https://github.com/5C-UoP/soc-drawer>`_ for all supported platforms.

:Development:

To install the development version you need to make sure you have the following dependencies installed.

- Git
- Flutter ^3.5.4

  - Android Studio
  - VS Code (Optional)
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

Running Tests
-------------

Tests are ran on each commit to every branch, and every merge commit. In order to merge a branch, the tests must pass. 
Tests should be developed for every new feature you have made. To run the tests please run the following snippet:

.. code-block:: console

     $ flutter test