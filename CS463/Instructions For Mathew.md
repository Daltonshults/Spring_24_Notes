Deleted the old docker database
* Created a new one
	* Name: algorhythms_db
	* Pass: AlgoRhythms0716199311211990

Feel free to create a new database if needed

The current implementation is here: https://github.com/Soundbendor/algorhythms/tree/algo_webserver

Database Initialization:
* `python manage.py collectstatic`: I don't think we need this because I am handling the requests for favico.ico with a view
* `python3 manage.py makemigrations`
* `python3 manage.py migrate`
* Then launch production server

Notes: 
* Make sure that Debug is set to False in the Django Settings File
* there are notes in the Settings file showing what should not be in there, or needs to be changed. Just search 'production' and you can find all of them
* I created a .env file to store environment vars, and I will send it to you in discord