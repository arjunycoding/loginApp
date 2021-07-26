Install
pip install pipenv 
pipevn install …
flask
psycopg2 or psycopg2-binary
flask-sqlalchemy
gunicorn
 Add Templates ->  Html
Add Static -> Css, and pictures
Add app.py outside all folders
What goes inside app.py:
from the flask module and from it import Flask, render_template and request
Make a variable called app and assign it to Flask(__name__)
Then do @app.route(‘/’) →if the url is a /
Make a function that renders the template that is the login, homepage, or form
Make a if loop that checks if __name__ is equal to ‘__main__’
Inside the if loop do app.run()
Add a ENV variable and assign it to ‘dev’
Make a if loop that checks if ENV is is equal to ‘dev’
Inside that set app.debug to True
Also set app.config['SQLALCHEMY_DATABASE_URI'] to postgresql://postgres:password@localhost/database name
Else set app.debug to False
Also set app.config['SQLALCHEMY_DATABASE_URI'] to ‘’
Outside the if loop set app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] to False
Then make a variable called db and assign it to SQLAlchemy(app) (check for spellings to!)
Under that make a class called whatever you want(also capitalize the first letter!) add a parameter of db.Model
Follow format:
__tablename__ = ‘whateverName’
column1 = db.Column(db.type(), primary_key = True)
column2 = db.Column(db.type())
def __init__(self, column1, column2)
self.column1 = column1
self.column2 = column2
After you make the class inside the pipenv shell run python
 Then run from app import db
After that run db.create_all() (check in the database if you have the table!)
Then make a if loop inside the function that takes in the creates the account
For the if loop check if db.session.query(name of database).filter(name of database.the field that has a primary key == the field that has a primary key).count() is equal to 0
Inside that make a variable call data and assign it to database name(column1, column2)
Make a new line and do db.session.add(data) this will add the  data to the database
After that do db.session.commit()
Finally, render template “the login page”
Then inside the login function create a variable called user and assign it AccountInfo.query.filter_by(email=email, password=password).first()
 Then make a if loop and check if user is None
If that runs true return render template “login.html”, massage”something that tells the user that the username or password is wrong”
Else  return render template “login.html”, user=user
Then inside loggedin.html write {{ user.column 1 }}

heroku login
heroku create <some name>
heroku addons:create heroku-postgresql:hobby-dev --app <some name>
heroku config --app <some name>
Copy and paste the url it gives to the else loop that sets app.debug to false
    app.config['SQLALCHEMY_DATABASE_URI'] = '<link give>' (link start: postgresql)
Switch ENV to ‘prod’
Then touch Procfile
In Procfile
web: gunicorn app:app
Create runtime.txt
Python-3.9.6
In terminal run pip freeze > requirements.txt
heroku git:remote -a <name of app>
git push heroku
Run heroku run python in terminal
From app import db
db.create_all()

YOU ARE DONE!