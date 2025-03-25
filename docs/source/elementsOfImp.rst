Elements Of Implementation
==========================

User Interface
--------------

Frontend
--------

Backend
-------
1P) The schema's structure was incorrect which means that when a user joined a project, there would be a row created in the ``project_members`` table but there would be no way of identifying the user hence why a 1:1 relationship to the ``online_user`` table was required. Additionally, the foreign keys for some of the tables were put in the wrong way round which made referencing hard.

1A) After we discovered this we made changes to the schema so that everything was correct.

2P) For the deployment of our database, we tried to use the university machine but due to the lack of privileges we were unable to host flask on the VM. This meant that we were not able to configure the psql database to allow connections from all IP's which meant that we were not able to connect to the VM from outside of the university (we had read-only permission) which made it hard for testing. Therefore we had to find an alternative which was Render. Render is a Cloud platform that we used to deploy our PSQL database to. This worked fine until we tested it at the university network. Due to the firewall configurations, we were unable to connect to Render which meant that we needed to find an alternative way of storing our database.

2A) Due to this, we had to chose to store our database locally. This has its own problems though as this means that there is no way for data to be synced across machines. However, we decided that since this is a prototype it will be fine to show the proof of concept.

3P) We had to think about how we were going to carry state & information between screens so for the home screen it would be able to display projects that the user is a part of after logging in or after signing up and joining a project.

3A) We opted to use the provider package since its an established method for carrying state between screens.