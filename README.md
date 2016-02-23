# Udacity Project 5: Configuring a Linux Web Server

Server IP: 52.36.80.206

SSH Port: 2200

Web Application URL: http://ec2-52-36-80-206.us-west-2.compute.amazonaws.com/

It should  be noted that the web app has been modified to work with postgres instead of sqlite, which was how my original project 3 was coded. I also had to make some adjustment to get around assumptions made about where the current working directory was (the uploads folder for example).

## Summary of Changes

* Created grader user.
* Added grader user entry to /etc/sudoers.d
* Updated package list and upgraded all installed packages.
* Installed the following packages for this assignment: 
  * apache2
  * postgresql
  * libapache2-mod-wsgi
  * git
* Installed the following packages as dependencies of the web application: 
  * python-httplib2
  * python-flask
  * python-sqlalchemy
  * python-psycopg2
  * python-oauth2client
* Confirmed that /etc/timezone reported UTC.
* Changed the configuration of /etc/ssh/sshd_config to listen on port 2200 instead of 22. Also confirming that password authentication was disabled and disabling remote login for root.
* Created a .wsgi file and modified the default apache vhost with the WSGI directive pointing to that wsgi file.
* Added a catalog postgres user (with a password) and database. Configured the application to connect with that password to the database.

## Third Party Resources

I used http://flask.pocoo.org/docs/0.10/deploying/mod_wsgi/ for guidance in writing the .wsgi file for my flask application.

I used http://stackoverflow.com/questions/8007176/500-error-without-anything-in-the-apache-logs as the basis of a modification to the .wsgi file to enable better logging when I was having difficulties getting the application to run.

I used https://mediatemple.net/community/products/dv/204643810/how-do-i-disable-ssh-login-for-the-root-user for guidance in disabling root logins.