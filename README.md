# Udacity Project 5: Configuring a Linux Web Server

Server IP: 52.36.80.206

SSH Port: 2200

Web Application URL: http://52.36.80.206/

Note that due to constraints put in place by Google in their OAuth2 implementation it is impossible to truly log in because they do not allow origins to be public IP addresses. This means that most of the actual functionality of the app does not work in this environment.

It should also be noted that the web app has been modified to work with postgres instead of sqlite, which was how my original project 3 was coded.

## Summary of Changes

Created grader user, added grader entry to /etc/sudoers.d

Updated package list and upgraded all installed packages.

Installed the following packages for this assignment: apache2, postgresql, libapache2-mod-wsgi, git

Installed the following packages as dependencies of the web application: python-httplib2, python-flask, python-sqlalchemy, python-psycopg2, python-oauth2client

Confirmed that /etc/timezone reported UTC.

Changed the configuration of /etc/ssh/sshd_config to listen on port 2200 instead of 22. Also confirming that password authentication was disabled and disabling remote login for root.

Created a .wsgi file and modified the default apache vhost with the WSGI directive pointing to that wsgi file.

Added a catalog postgres user (with a password) and database. Configured the application to connect with that password to the database.

## Third Party Resources

I used http://flask.pocoo.org/docs/0.10/deploying/mod_wsgi/ for guidance in writing the .wsgi file for my flask application.

I used http://stackoverflow.com/questions/8007176/500-error-without-anything-in-the-apache-logs as the basis of a modification to the .wsgi file to enable better logging when I was having difficulties getting the application to run.

I used https://mediatemple.net/community/products/dv/204643810/how-do-i-disable-ssh-login-for-the-root-user for guidance in disabling root logins.