dkd/docker-typo3
============================

Out-of-the-box TYPO3 docker image which can be linked to MySQL.


CREDITS
------------------
This image is highly inspired by (tutum-docker-wordpress-nosql)[https://registry.hub.docker.com/u/tutum/wordpress-stackable/]!


Usage (standalone)
------------------



This image needs an external MySQL server or linked MySQL container. To create a MySQL container:

    docker run -d -e MYSQL_PASS="<your_password>" --name db -p 3306:3306 tutum/mysql:5.5

To run TYPO3 by linking to the database created above:

    docker run -d --link db:db -e DB_PASS="<your_password>" -p 80:80 thinkopenat/typo3-git-master

Now, you can use your web browser to access TYPO3 from the the follow address:

    http://localhost/typo3

User is "admin" and password is "password".

When you have already an apache running on your local machine you can start the docker container differently:

    docker run -d --link db:db -e DB_PASS="<your_password>" -p 8080:80 thinkopenat/typo3-git-master

and the new TYPO3 instance will be available at http://localhost:8080/typo3/

Documentation
-------------

Some additional documentation can be found here: https://wiki.typo3.org/TYPO3-Docker
