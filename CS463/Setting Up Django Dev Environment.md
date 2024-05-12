These are the instructions to get the Django API running on your local machine. These steps assume that PostgreSQL will already be installed on your machine. The PostgreSQL instructions can be found [here](https://www.postgresql.org/docs/current/tutorial-install.html) These steps assume you are going to be running PostgreSQL on your local machine, and not within a Docker container. 
1. Clone from the [GitHub](https://github.com/Soundbendor/algorhythms)
	* Steps to clone only the `webserver` folder
		1. `git clone --filter=blob:none --no-checkout git@github.com:Soundbendor/algorhythms.git <local-directory>`
		2. `cd <local-directory>`
		3. `git sparse-checkout init --cone`
		4. `git sparse-checkout set webserver`
		5. `git checkout`
2. Install the requirements from the `requirements.txt` file that is located at `/webserver/requirements.txt`
	* Those with ARM architectures need to install `graphviz` using brew. Then `graphiviz` must be added to the path otherwise the `graphv.h` may not be found. [Help](https://pygraphviz.github.io/documentation/stable/install.html#macos)
3. Setup the database
	1. Login to Postgres using `psql -U postgres -d postgres`
	2. Create a database `CREATE DATABASE <database-name>`
		1. The database name should match what is contained within your Django settings file
	3. Exit Postgres using `\q`
4. Initialize the database: Navigate to the folder that contains the `manage.py` file. This should be in the root directory of the `webserver` folder. If a sparse clone was done, it should be contained within the folder that you cloned into.
	1. Navigate to `manage.py`
	2. Make the migrations file: Run the command `python3 manage.py makemigrations`
	3. Migrate the data base: Run the command `python3 manage.py migrate`
		1. If you are having issues, and your Django is replying with `No changes detected` you could have a migrations folder already. It would be contained within `/webserver/algorhythms/migrations` it should have a name like `0001_initial.py`. You can delete this file **IF** your database is empty. Once the file has been deleted repeat these steps. **ONLY DELETE THIS FILE IF THE DATABASE IS EMPTY AND YOU DO NOT NEED IT. THESE FILES TRACK HOW THE DATABASE CHANGES AND HELPS MANAGE THE MIGRATIONS THEY ARE IMPORTANT, BUT GET IN THE WAY WHEN INITIALIZING**
	4. Create a superuser: run the command: `python3 manage.py createsuperuser` this will be your database admin
5. Populate the database: You can use the generate fake data script contained within the `webserver` folder, or you can populate it with your real data. `generate_exercises.py` can be run to generate exercises from a CSV. 