# Contact Management Application
Contact management application that allows an employee to store and management and management client contact numbers.

# How to Install Dependencies
pip3 install virtualenv <br/>
mkdir -p ~/.virtualenvs <br/>
pip3 install virtualenvwrapper <br/>
mkvirtualenv contact_env <br/>
If the virtual environment is not activated, type "workon contact_env" <br/> 
pip3 install -r requirements.txt

# Setup the application
cd contactManager/contactManager
To create DB model: python manage.py makemigrations contactApp<br/>
python manage.py migrate <br/>
python manage.py createsuperuser <br/>
Follows the prompts to create the user account up until it is successfully created <br/>

# How to Run Application
workon contact_env <br/>
python manage.py runserver

# Creating access token for use to access the services
Open browser or api testing application: http://127.0.0.1:8000/api/auth/access-token/ <br/>
Prompted for username and password. <br/>
When successfully validated, an access-token and a refresh-token will be created. <br/>
Refresh token is used for access-token creation since access-token is only valid for 5 minutes while refresh-token is valid for 24 hours. <br/>

# Accessing the web services

Open api testing application(i.e. Postman)<br/>
Type the following address in the request url section: http://127.0.0.1:8000/api <br/>
Set request authorisation using the generated access-token.<br/>
Available services: <br/>
1. /api/contact/ - accept both get and post request <br/>
  - GET: retrieve client contact number profile given the mobile_number.<br/>
  - POST: create client contact number account/prfile.<br/>
2. /api/auth/access-token/ - accept post request <br/>
3. /api/auth/refresh-token/ - accept post request <br/>
4. /admin/ - goes to the admin login page<br/>
 - POST: If refresh token is valid, this service will generate a new access-token.<br/>



