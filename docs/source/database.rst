==================
Database
===================
The database is written in SQLite.

The database is where all the data is stored to aid the frontend application. 
The database is normalized and uses foreign key relationships, this helps maintain the data integrity and consistency. 
The database consists of five tables: house_info, user_info, chores, messages, and shopping_list.

house_info table:

-	This table holds general information about the house/ houses.
-	It holds the following fields: 
o	house_id (SERIAL) – The SERIAL data type is used here to ensure that the house has a unique identifier, Avoiding manual input means that no two houses can have the same primary key.
o	house_nickname (VARCHAR(15)) – VARCHAR(15) is used because it is only storing short nicknames.
o	 house_address (VARCHAR(50)) – VARCHAR(50) is used because 50 characters should be enough to store an address.
o	city (VARCHAR(50)) – VARTCHAR(50) is used because city names can vairy in length this should be enough for all cities.
o	 country (VARCHAR(56)) – VARCHAR(50) is used as it can fit all country’s names in it. 
o	 postcode (CHAR(10)) – CAHR(10) is used because postcodes are normally a fixed length. The use of CHAR makes sure no extra storage is used. 
o	 and bin_code (VARCHAR(30)). – VARCHAR(30) this ensures there is enough space for all bin codes as they can change a lot in length.
o	 This is the core information needed to locate the house / know which house is which if multiple.
-	This table also allows for the connection between other features within a house for example the group chat (messages) the message will go to the house_id.

user_info table:

-	This table holds the personal information and login details for each user.
-	It holds the following fields:
o	user_id (SERIAL) – The SERIAL data type is used so that all users have a unique identifier, this helps when users are referenced in other tables.
o	house_id (INT) – Used as a foreign key to reference the house_info table, this is how the house_info table and user_info table are linked.
o	first_name (VARCHAR(15) – VARCHAR(15) is used to cover most first names.
o	 last_name (VARCHAR(20)) – VARCHAR(20) is used to cover most last names.
o	username (VARCHAR(15)) – VARCHAR(15) is used because it is more than enough characters to for a username while making sure the length of the username is still manageable. 
o	password (VARCHAR(128)) – VARCHAR(128) is used because it allows for enough characters for most encrypted passwords.
o	email (VARCHAR(50)) – VARCHAR(50) is used because it has enough characters to store most email addresses.
o	date_of_birth (DATE) – DATE is used because it stores the data in a YYYY-MM-DD format.
-	The house_id is a foreign key from the house_info table which is used to link each specific user to their house. 

chores table:
              
-	This table is where data can be stored on what chores each user has been assigned and what has been completed and not completed.
-	It holds the following fields: 
o	chore_id (SERIAL) – SERIAL is used so that each chore has a unique id.
o	 user_id (INT) –  Referenced to the user_info table, allowing a user to be assigned a chore.
o	chore_name (VARCHAR(20)) – VARCHAR(20) 20 characters is enough to keep it readable and concise. 
o	 chore_description (VARCHAR(50)) – VARCHAR(50) is used as it allows for a short description.
o	due_date (DATE) – DATE is used as it is stored in the format YYYY-MM-DD.
o	assigned_date (DATE) – DATE is used as it is stored in the format YYYY-MM-DD.
o	 completed (BOOLEAN) – BOOLEAN is used because it is either true or false. 
-	The user_id is a foreign key from the user_info table, this is what allows a chore to be assigned to a specific user. 
              
messages table:
              
-	This table is where messaegs are stored coming from users within the same house, allowing the group message feature to work.
-	It holds the following fields:
o	message_id (SERIAL) – SERIAL is used to provide each message with a unique id.
o	house_id (INT) – Reference to the house_info table. 
o	 user_id (INT) – Refrenced to the user_info table.
o	 message_text (TEXT) – TEXT is used so that the message can be any length long or short.
o	 and message_date (TIMESTAMP) – TIMESTAMP ensures the exact date and time is stored.
-	The house_id is a foreign key from the house_info table, allowing the message to be shown only within the specific house. The user_id is a foreign key from the user_info, allowing the user to be linked to the messages they send. 
              
shopping_list table: 
              
-	This table is where users can add things the need to be brought for the house. The list will be visible to everyone in the house and anyone in the house can add to it. 
-	It holds the following fields:
o	 item_id (SERIAL) – Each item will have a unique id for every item on the shopping list.
o	house_id (INT) – Reference from house_info.
o	Who_paid (VARCHAR(30)) – allows enough space for the name of who paid.
o	item_name (VARCHAR(100)) -  Allows enough space for most names of the items.
o	item_quantity (INT) – INT allows for the number of products that need to be brought to be stored.
o	 item_price (DECIMAL(10,2)) – DECIMAL(10,2) will allow for the price to be represented correctly.
o	 item_brought (BOOLEAN) – BOOLEAN because it can either be true or false.
o	user_id (INT) – Reference to the user_info table. 
-	The house_id foreign key from house_info allows the shopping list to be specific to each house allowing all users in the house to see the shopping list. The users_id foreign key from the user_info table allows the user that brought the product be credited for it / displayed for other housemates to see. 


Data Dictionary:

house_info:

Attribute_name -  Key -  Index -  Data Type and Size -  Domains and Constarints -  FK Refrences -  Description
house_id       -  PK   -       -  SERIAL             -                          -               -  The unique identifier for the house 
house_nickname -       -       -  VARCHAR(15)        -                          -               -  A nickname for the house
house_address  -       -       -  VARCHAR(30)        -  NOT NULL, UNIQUE        -               -  The address of the house 
city           -       -       -  VARCHAR(30)        -  NOT NULL                -               -  The city the house is located in 
postcode       -       -       -  VARCHAR(7)         -  NOT NULL                -               -  The postcode of the house 
Country         -       -       -  VARCHAR(30)        -  NOT NULL                -              -  The country the house is located in 
              
user_info: 

Attribute_name -  Key -  Index -  Data Type and Size -  Domains and Constarints -  FK Refrences -  Description
user_id        -  PK  -        -  SERIAL             -                          -               -  Unique identifier for the user 
house_id       -  FK  -        -  INT                -                          -  house_info   -  Unique identifier for the house the user is attached to
username       -      -        -  VARCHAR(15)        -  NOT NULL, UNIQUE        -               -  The users username 
first_name     -      -        -  VARCHAR(15)        -  NOT NULL                -               -  The users first name 
last_name      -      -        -  VARCHAR(20)        -  NOT NULL                -               -  The users last name 
email          -      -        -  VARCHAR(50)        -  NOT NULL                -               -  The users email address
date_of_birth  -      -        -  DATE               -  NOT NULL                -               -  The users date of birth 
password       -      -        -  VARCHAR(128)       -  NOT NULL                -               -  The users password 

chores:

Attribute_name -  Key -  Index -  Data Type and Size -  Domains and Constarints -  FK Refrences -  Description
chore_id       -  PK  -        -  SERIAL             -                          -               -  Unique identifer for the chore
user_id        -  FK  -        -  INT                -                          -  user_info    -  Unique identifer for the user attached to the chore
chore_name     -      -        -  VARCHAR(20)        -  NOT NULL                -               -  The name of the chore
chore_description -   -        -  VARCHAR(50)        -  NOT NULL                -               -  A description of the chore 
due_date       -      -        -  DATE               -  NOT NULL                -               -  When the chore is due to be completed by
assigned_date  -      -        -  DATE               -  NOT NULL                -               -  When the chore was assigned to the user 
completed      -      -        -  BOOLEAN            -  NOT NULL, DEFUALT FALSE -               -  If the chore has been completed or not 

messages:

Attribute_name -  Key -  Index -  Data Type and Size -  Domains and Constarints -  FK Refrences -  Description
message_id     -  PK  -        -  SERIAL             -                          -               -  Unique identifier for the message 
house_id       -  FK  -        -  INT                -                          -  house_info   -  Unique identifier for the house the message is attached to
user_id        -  FK  -        -  INT                -                          -  user_info    -  Unique identifier for the user the message is attached to
message_text   -      -        -  TEXT               -  NOT NULL                -               -  The text inside the message 
message_date   -      -        -  TIMESTAMP          -  NOT NULL                -               -  The time the message was sent

shopping_list:

Attribute_name -  Key -  Index -  Data Type and Size -  Domains and Constarints -  FK Refrences -  Description
item_name      -  PK  -        -  SERIAL             -                          -               -  A unique identifier for the item
house_id       -  FK  -        -  INT                -                          -  house_info   -  Unique identifier for the house the item is attached to
user_id        -  FK  -        -  INT                -                          -  user_info    -  Unique identifier for the user the item is attached to
who_paid       -      -        -  VARCHAR(30)        -                          -               -  The person who paid for the item item, if its not been paid for value = "
item_name      -      -        -  VARCHAR(100)       -  NOT NULL                -               -  Name of the item required 
item_quantity  -      -        -  INT                -  NOT NULL                -               -  How many of the item is needed
item_price     -      -        -  DECIMAL(10,2)      -  NOT NULL                -               -  How much the user spent on the item
item_brought   -      -        -  BOOLEAN            -  NOT NULL, DEFULT FALSE  -               -  Has the item been purchesed 
