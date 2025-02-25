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