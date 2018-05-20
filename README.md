# Deploying flask application using PostgreSQL to AWS Lightsail instance
Take a baseline installation of a Linux server and prepare it to host web applications. Secure your server from a number of attack vectors, install and configure a database server, and deploy an existing web applications onto it.
## Basic Information
IP Address: 18.217.173.48
PORT: 2200
SSH Key: I included the private key in the "Notes to Reviewer" section when I submitted my project.
## Step 1
Created a default instance of a Linux server on Amazon Lightsail, and then updated all currently installed packages by running:

    $ sudo apt-get update
then

    $ sudo apt-get upgrade
## Step 2
Configure the firewall by running the following commands:

    $ sudo ufw status
this is to insure that the firewall is inactive.
Then block all incoming connections and allow all outgoing connections by running:

    $ sudo ufw default deny incoming
    $ sudo ufw allow outgoing
Per the project rubric the following ports were configured; 2200 for SSH, 80 for HTTP, and 123 for NTP. This was accomplished by running:

    $ sudo ufw allow 2200/tcp
    $ sudo ufw allow www
    $ sudo ufw allow ntp
    $ sudo ufw enabled
## Step 3
Create user grader to allow Udacity's reviewer to access the project. Then configure user grader for sudo and generate key pair.

    $ sudo adduser grader
    $ sudo nano /etc/sudoers.d/grader
Then add `grader ALL=(ALL:ALL) ALL` to the newly created file /etc/sudoers.d/grader.

## Acknowledgements
Udacity forums for tons of invaluable assistance.
