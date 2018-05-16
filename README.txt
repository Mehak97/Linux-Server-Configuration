IP address:
13.59.67.215

to login:
ssh grader@13.59.67.215 -p 2200 -i grader

User Created:
A grader user created providing a sudo access.Allowing only it to login to the site regardless of other remote users.

Setup Firewall:
A firewall is setup to communicate with the server.
Allowing http,tcp,ntp ports to communicate with the server.

Changing the port from 22 to 2200.

Inorder To Secure our site from forgery users ,provide key-pair authentication despite of password authentication.
To generate key-pair authentication:
ssh key-gen
A private and public key has been generated.To use a key to log in to system,the content of public key has to be added inside the .ssh/authorrized_keys file.

After,providing and setting up key-pair based authentication ,we have to disable password authentication.
In order, to disable:
sudo nano /etc/ssh/sshd_config
PasswordAuthentication No

Then,restart the service using:
ssh service restart

Now,grader sholud be able to login directly regadless of the password set before and disallowing other users to log in ot the system.

Cloning the Repo:
git clone https://github.com/Mehak97/Item-Catalog.git

Installing Apache Server to handle HTTP server request:
sudo apt-get install apache2

Inorder to access python file,install 
sudo apt-get install libapache2-mod-wsgi

Create a directory named /var/www/DirectoryName and copy the folder containing the project.
And filename.wsgi add your secret_key and insert youor directory location

And enable the wsgi file, so that apache gets to know which file to run and search upto.
In the wsgi file,include 
<Directory ItemCatalog>
    WSGIProcessGroup project_server
    WSGIApplicationGroup %{GLOBAL}
    Order deny,allow
    Allow from all
</Directory>
by telling apache to configue the wsgi file and restart the service.

Installing POSTGRESQL:
sudo apt-get install postgresql 
Create a user and setup the database.Revoke other users and allow only the created user to access.
Run database_setup.py and lotsofmenues.py file to setup the database and install the required libraries to run the server.

Change the relative path provided by client_secrets.json to absolute path for apache to recognize.

restart the server.

REQUIRED MODULES:
1. sqlalchemy
2. flask
3. oauth2.reqiured
4. pip

EXTERNAL SOURCES:
1. POSTGRESQL documentation
2. StackoverFlow







