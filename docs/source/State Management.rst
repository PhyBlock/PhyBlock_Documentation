State Management
===============
.. note:: This page is currently empty. Please check back later for updates.

## State Management

Overview

The state management in this application is primarily manual and service-based, utilizing Dart classes and setState() within Flutter widgets where needed. 

The app avoids using external state management libraries such as Provider, Riverpod, or Bloc in favor of a more lightweight and understandable architecture suited to the app’s current complexity.

**AccountManager

The AccountManager class is responsible for managing the user account state, interacting with the database, and handling user-related information such as login, 
logout, account creation, and account updates.

**PointsManager

The PointsManager handles internal state for user progress, including total points, completed points, and pass thresholds based on difficulty.

All state—such as maxPoints, currentPoints, and completedTasks — is self-contained, and updated through methods like addTask, completeTask, and removeTask.

