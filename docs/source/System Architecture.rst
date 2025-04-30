System Architecture
===================
.. note:: This page is currently under development. Please check back later for updates.

The app has a 3-layer architecture. 

******
Presentation Layer
******
The GUI is comprised of a collection of "screens" (occasionally "page" is used synomously). 
The code for each screen is written in its own file in ``lib/userInterfaces``.

Each screen is comprised of between 1 and 3 objects, depending on the nature of the screen. 

Screens which do not store state are comprised primarily of 1 object,
which extends the ``StatelessWidget`` class. 
Such screens include:
- ``LogInScreen`` in ``log_in.dart``

- ``ProfileScreen`` in ``profile.dart``

- ``SettingsPage`` in ``settings_page.dart``

- ``WelcomeScreen`` in ``start_up.dart``

``TaskDetails`` in ``task_details.dart`` is similar to the other screens mentioned in this category, but it is not a full screen. 
It overlays a portion of the home screen (``ScheduleScreen``). 

Screens which store state are primarily comprised of 2 objects. 
The first extends the ``StatefulWidget`` class, and the second extends the ``State<ScreenName>`` class 
(where ``ScreenName`` is the name of that screen's first object.) 
Such screens include:
- ``AddTaskScreen`` in ``add_task.dart``

- ``CategoryRankingScreen`` in ``category_ranking.dart``

- ``DifficultyPage`` in ``difficulty_page.dart``

- ``ScheduleScreen`` in ``home.dart`` (this is the home screen)

- ``MindfulnessScreen`` in ``mindfulness_page.dart``

- ``NotificationScreen`` in ``notification_page.dart``

- ``SignUpScreen`` in ``sign_up.dart``

Some screens also have an additional object to implement a navigation bar (NavBar).


******
Business Logic Layer
******

The business logic is handled by several "managers". 
These include an ``AccountManager``, a ``ScheduleManager``, an ``AlarmManager``, a ``NotificationManager`` and a ``PointsManager``. 

The ``AccountManager`` and ``ScheduleManager``, being particularly complex, are divided across several files. 
These managers are defined by an interface, which specifies the methods they provide. 
This simplifies development as it provides a consistent API to be used by the presentation layer.

TODO: TOC for this page
TODO: Breakdown of functionality / interaction of these different managers?