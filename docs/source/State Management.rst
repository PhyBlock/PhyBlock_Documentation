State Management
===============

Overview

The state management in this application is primarily manual and service-based, utilizing Dart classes and setState() within Flutter widgets where needed. 

The app avoids using external state management libraries such as Provider, Riverpod, or Bloc in favor of a more lightweight and understandable architecture suited to the app’s current complexity.

**AccountManager

The AccountManager class is responsible for managing the user account state, interacting with the database, and handling user-related information.

It maintains a single piece of mutable state 'UserAccountModel? userAccount', this holds the current user's account data or null if not signed in.

These methods change the internal state:

login(...) - Fetches user data from the database and sets userAccounts.

logout() - Clears userAccount.

createAccount(..) - Creates a new user and sets userAccount.

deleteAccount(...) - Deletes the account and clears userAccount.

updateAccount(...) - Replaces userAccount and persists changes.

**PointsManager

The PointsManager handles internal state for user progress, including total points, completed points, and pass thresholds based on difficulty.

All state—such as maxPoints, currentPoints, and completedTasks — is self-contained, and updated through methods like addTask, completeTask, and removeTask.

**ScheduleManager

The ScheduleManager class relies on manual, internal state management as well via class members and callbacks.

It exposes and mutates state via method calls such as addTask, deleteTask, edittask etc.

It uses callback functions for UI interaction such as 
- displayErrorCallback(String) : Notifies the UI of errors
- userBinarySelectCallback(TaskModel, TaskModel, String) : Request user input on task selection.

The app uses manual, class-based internal state management, where each manager class maintains its own internal state 
and exposes methods to mutate or retrieve that state.


