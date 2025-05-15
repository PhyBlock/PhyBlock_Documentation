===================================
Home Page
===================================
Unit Explanation
===================================

The home page acts as the main page that is initially displayed once the user has logged into their account on the app. This page contains the ability to navigate to different areas within the context of the application. As such, this page is treated as the central hub for the user.

===================================
Design:
===================================

The home page is designed to be simple and easy to understand. As such, we have made sure the display is not cluttered and that all the buttons and functions are easy to see and understand. The more frequently used functions (calendar, rota, group chat and shopping list) are accessible through the main page. To keep the screen clear and to avoid clutter, we opted to put lesser used functionalities (such as action log, settings, user info, etc.) in a separate drawer that can be displayed when the user wants to preserve visual clarity
All the buttons are also labelled with appropriate names or icons that correspond to the page they lead to. This allows the user to easily navigate to their desired page without needing any prior knowledge of our system

===================================
Code
===================================

The main bulk of the code for this page is the buttons code. We used IconButtons to build and program each of the buttons. All the buttons used navigation routes that were mapped out and referenced in the program’s main function. The button would call the Navigator.pushNamed function that would then take the dedicated routes as the context which would tell the program which page the button should lead to. The buttons that are displayed in the main section of the home page are built using a list builder which again would pass the name of the button and the route context (with the only exception being the calendar button that is built manually). The rest of the buttons are built into a drawer which acts as a collapsable sidebar. 

==================================
Testing 
==================================

The only components that needed testing for this was the use of buttons. In order to test this, we built automated test cases that would test the functionality by simulating a button press. This was done using dart widget testing. We simulated a button being pressed which would then lead to the next page. The test then checked the title of the page to make sure it matched up with the expected outcome.
