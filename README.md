# AirBnB clone - The console

<p align="center">
    <img src="https://i.imgur.com/JOhaZ5m.png">
</p>

## Description

In this project we expanded on the last AirBnB project, which focused on the console, and added SQLALchmeny functionality to make sure class attribute IDs could be linked together.
To start, we forked [this repository](https://github.com/yook00627/AirBnB_clone), which acted as a base for the rest of our code.

Using this repo, the developer can either store their data in a file storage system. Part of our task was to refactor this codebase to include MySQL integration via SQLAlchemy.

## Background Context
Environment variables will be your best friend for this project!

* `HBNB_ENV`: running environment. It can be “dev” or “test” for the moment (“production” soon!)
* `HBNB_MYSQL_USER`: the username of your MySQL
* `HBNB_MYSQL_PWD`: the password of your MySQL
* `HBNB_MYSQL_HOST`: the hostname of your MySQL
* `HBNB_MYSQL_DB`: the database name of your MySQL
* `HBNB_TYPE_STORAGE`: the type of storage used. It can be “file” (using `FileStorage`) or `db` (using `DBStorage`)

## Resources
* [cmd module](https://docs.python.org/3.4/library/cmd.html)
* [packages](https://intranet.hbtn.io/concepts/66)
* [unittest module](https://docs.python.org/3.4/library/unittest.html#module-unittest)
* [args/kwargs](https://pythontips.com/2013/08/04/args-and-kwargs-in-python-explained/)
* [SQLAlchemy tutorial](https://docs.sqlalchemy.org/en/13/orm/tutorial.html)
* [How To Create a New User and Grant Permissions in MySQL](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)
* [Jimmy’s (My)SQL Cheat Sheet](https://gist.githubusercontent.com/MasterProgrammer200/771e877ff56a4e75f32d/raw/a66990e0935dc95029a1bba05db07c57cf231d9f/mySQLCheatSheet.SQL)
* [Python3 and environment variables](https://docs.python.org/3/library/os.html?highlight=env#os.getenv)
* [Object Relational Mapping with Python’s SQL Alchemy](https://medium.com/@eightlimbed/object-relational-mapping-with-pythons-sql-alchemy-1af658b02679)
* [SQLAlchemy](https://docs.sqlalchemy.org/en/13/)
* [MySQL 5.7 SQL Statement Syntax](https://dev.mysql.com/doc/refman/5.7/en/sql-syntax.html)

## Requirements

### Python Scripts
* All your files will be interpreted/compiled on Ubuntu 14.04 LTS using `python3` (version 3.4.3)
* All your files should end with a new line
* The first line of all your files should be exactly `#!/usr/bin/python3`
* A `README.md` file, at the root of the folder of the project, is mandatory
* Your code should use the `PEP 8` style (version `1.7.*`)
* All your files must be executable
* The length of your files will be tested using `wc`
* All your modules should have documentation (`python3 -c 'print(__import__("my_module").__doc__)'`)
* All your classes should have documentation (`python3 -c 'print(__import__("my_module").MyClass.__doc__)'`)
* All your functions (inside and outside a class) should have documentation (`python3 -c 'print(__import__("my_module").my_function.__doc__)'` and `python3 -c 'print(__import__("my_module").MyClass.my_function.__doc__)'`)

### Python Unit Tests
* All your files should end with a new line
* All your test files should be inside a folder `tests`
* You have to use the unittest module
* All your test files should be python files (extension: `.py`)
* All your test files and folders should start by `test_`
* Your file organization in the tests folder should be the same as your project: ex: for `models/base_model.py`, unit tests must be in: `tests/test_models/test_base_model.py`
* All your tests should be executed by using this command: `python3 -m unittest discover tests`
* You can also test file by file by using this command: `python3 -m unittest tests/test_models/test_base_model.py`
* All your modules should have documentation (`python3 -c 'print(__import__("my_module").__doc__)'`)
* All your classes should have documentation (`python3 -c 'print(__import__("my_module").MyClass.__doc__)'`)
* All your functions (inside and outside a class) should have documentation (`python3 -c 'print(__import__("my_module").my_function.__doc__)'` and `python3 -c 'print(__import__("my_module").MyClass.my_function.__doc__)')`
* We strongly encourage you to work together on test cases, so that you don’t miss any edge cases

### SQL Scripts
* All your files will be executed on Ubuntu 14.04 LTS using `MySQL 5.7` (version 5.7.8-rc)
* Your files will be executed with `SQLAlchemy` version `1.2.x`
* All your files should end with a new line
* All your SQL queries should have a comment just before (i.e. syntax above)
* All your files should start by a comment describing the task
* All SQL keywords should be in uppercase (`SELECT`, `WHERE`…)
* A `README.md` file, at the root of the folder of the project, is mandatory
* The length of your files will be tested using `wc`

## More Info
![server pic](https://medium.com/markdown-monster-blog/getting-images-into-markdown-documents-and-weblog-posts-with-markdown-monster-9ec6f353d8ec)

### Comments for your SQL file:
```
$ cat my_script.sql
-- first 3 students in the Batch ID=3
-- because Batch 3 is the best!
SELECT id, name FROM students WHERE batch_id = 3 ORDER BY created_at DESC LIMIT 3;
$
```

---
## Models

The folder [models](https://github.com/MCavigli/AirBnB_clone_v2/tree/master/models) contains all the classes used in this project.

File | Description | Attributes
---- | ----------- | ----------
[base_model.py](./models/base_model.py) | BaseModel class for all the other classes | id, created_at, updated_at
[user.py](./models/user.py) | User class for future user information | email, password, first_name, last_name
[amenity.py](./models/amenity.py) | Amenity class for future amenity information | name
[city.py](./models/city.py) | City class for future location information | state_id, name
[state.py](./models/state.py) | State class for future location information | name
[place.py](./models/place.py) | Place class for future accomodation information | city_id, user_id, name, description, number_rooms, number_bathrooms, max_guest, price_by_night, latitude, longitude, amenity_ids
[review.py](./models/review.py) | Review class for future user/host review information | place_id, user_id, text

## Storage

The [engine](https://github.com/MCavigli/AirBnB_clone_v2/tree/master/models/engine) folder holds two files for different storage methods.

File | Description
---- | ----------
[file_storage.py](https://github.com/MCavigli/AirBnB_clone_v2/blob/master/models/engine/file_storage.py) | Serializes and deserializes instances to and from  a JSON file)
[db_storage.py](https://github.com/MCavigli/AirBnB_clone_v2/blob/master/models/engine/db_storage.py) | Initializes a MySQL database that stores instances

## Tests

All the code is tested with the **unittest** module.
The test for the classes are in the [test_models](./tests/test_models/) folder.

## Authors
[Yordanos Girma](https://github.com/yordigenet) - yordigenet@gmail.com
