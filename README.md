# Deploying flask application using PostgreSQL to AWS Lightsail instance
Take a baseline installation of a Linux server and prepare it to host web applications. Secure your server from a number of attack vectors, install and configure a database server, and deploy an existing web applications onto it.
## Basic Information
IP Address: 18.217.173.48
PORT: 2200
SSH Key: I included the private key in the "Notes to Reviewer" section when I submitted my project.
Installed software is Python, Apache, and PostgreSQL.
## Step 1 - Get the server running
Created a default instance of a Linux server on Amazon Lightsail, and then updated all currently installed packages by running:

    $ sudo apt-get update
then

    $ sudo apt-get upgrade
## Step 2 - Configure the firewall
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
## Step 3 - Setup new user grader
Create user grader to allow Udacity's reviewer to access the project. Then configure user grader for sudo and generate key pair.

    $ sudo adduser grader
    $ sudo nano /etc/sudoers.d/grader
Then add `grader ALL=(ALL:ALL) ALL` to the newly created file /etc/sudoers.d/grader.

Next a ssh key pair needs to be generated for user grader. This is accomplished using the following series of commands on a local machine:

    /home/<username> $ mkdir .ssh
    /home/<username> $ chown <username>:<username> /home/<username>/.ssh
    /home/<username> $ cd .ssh
    /home/<username>/.ssh $ ssh-keygen
The `ssh-keygen` command will prompt the user to enter a file name for the keys and will create a newfile and newfile.pub with the private and public keys.

Copy the contents of the newfile.pub file. Then ssh back into the Lightsail instance as the user grader. This can be accomplished by logging in as the ubuntu user and running:

    $ sudo su - grader

Then run the following commands to set the proper user permissions to account for Amazon policies:

    $ sudo mkdir .ssh
    $ sudo chown grader:grader /home/grader/.ssh
    $ sudo chmod 700 /home/grader/.ssh
Then cd into the '.ssh' directory and paste the contents of the public generated previously by running:

    $ sudo nano authorized_keys
    $ sudo chmod 400 authorized_keys


 
## Acknowledgements
Udacity forums for tons of invaluable assistance.

> Written with [StackEdit](https://stackedit.io/).
