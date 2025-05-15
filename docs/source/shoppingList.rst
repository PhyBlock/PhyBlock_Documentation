===================================
Shopping list
===================================

The shopping list feature allows users to add items the household needs to buy and share them with the other members
of the house. Each item holds a name and quanity for the user.

There is also a button which takes the user to the spending page allowing them to see what they have spent over the course of
thier tenancy.


Design
================

Code
================

Classes
================


Testing
================
All tests are done within the datachecks class.

All automated tests for the shopping list are in the shoppingList_test.dart.

All tests are detailed within the testing plan.

Item creation:
-----------------
Items are checked and created using the addShoppingItem method. 
There is two parameters the collected quantity and name of the item, firstly theres a check for a quantity given,
if there is no input the item quantity is set to 0. 
Then theres a check to ensure that the quantity is an integer value if not the check fails.
Finally it checks the item name is within the character set.

Adding a spent cost:
-----------------------
All costs are checked with the addShoppingItem method.
There is one parameter called cost. 
Theres a check for an empty valid which will lead to an automatic fail. Then it checks that
the cost is a valid double within the allowed range. Then the number of decimal points are checked

