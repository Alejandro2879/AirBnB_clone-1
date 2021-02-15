# 0x00. AirBnB clone - The console
------------

![Logo AirBnb](https://i.ibb.co/BT08MTv/65f4a1dd9c51265f49d0.png)

------------
## Overview
------------
The goal of the project is to deploy on your server a simple copy of the AirBnB website.
Some of the functions that will cover the fundamental concepts will be implemented of the higher level programming track.
Al final se obtendra una aplicacion web completa compuesta por:
 - A command interpreter to manipulate data without a visual interface, like in a    Shell (perfect for development and debugging)
 - A website (the front-end) that shows the final product to everybody: static and    dynamic
 - A database or files that store data (data = objects)
 - An API that provides a communication interface between the front-end and your      data (retrieve, create, delete, update them
 
In this project we will do the first part.

------------
# The console
------------

 - create your data model
 - manage (create, update, destroy, etc) objects via a console / command interpreter
 - store and persist objects to a file (JSON file)

The first piece is to manipulate a powerful storage system. This storage engine will give us an abstraction between “My object” and “How they are stored and persisted”. 

This means: from your console code (the command interpreter itself)

This abstraction will also allow you to change the type of storage easily without updating all of your codebase.
The console will be a tool to validate this storage engine
![](https://i.ibb.co/Qk2QD5S/815046647d23428a14ca.png)

------------
### target of command interpreter
------------

 - Create and save a new object.(Example: New User, ew place, new atrribute, etc)
 - Read Objects created from a json file
 - Interact and modify the object (show, count, modify, etc)
 - Update object attributes
 - Destroy an object

------------
## Table of Content
------------

 - [Environment](#environment)
 - [Installation](#installation)
 - [File Descriptions](#file-descriptions)
 - [Usage](#usage)
 - [Examples of use](#examples)
 - [Bugs](#bugs)
 - [Authors](#authors)
 - [License](#license)

------------

## Environment

------------

This project is interpreted/tested on Ubuntu 14.04 LTS using python3 (version 3.4.3)

------------

## Installation

------------

 - Clone this repository: `git clone "https://github.com/aristizabaru/AirBnB_clone.git"`
 - Run **interactive** mode: `(./console.py)`
```
$ ./console.py
(hbnb) help
Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb) 
(hbnb) 
(hbnb) quit
$
```
 - Run **non interactive** mode: `echo "<command>" | ./console.py`
```
$ echo "help" | ./console.py
(hbnb)
Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb) 
$
$ cat test_help
help
$
$ cat test_help | ./console.py
(hbnb)
Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb) 
$
```
------------

## File Descriptions

------------

[console.py](console.py): Contains the entry point of the command interpreter. The commands accepted by the console are:

 - `create`: Creates a new instance of a model.
   - Ussage: `create <class name>`
 - `count`: Return number of istances of a class.
   - Ussage: `count <class name>`
   - Ussage `[optional]: <class name>.all()`
 - `show`: Prints the string representation of an instance based on the class name.
   - Ussage: `show <class name> <id>`
 - `destroy`: Deletes an instance based on the classname and id.
   - Ussage: `destroy <class name> <id>`
 - `all`: Prints all string representation of all instances based or not on the       class name.
   - Ussage: `all <class name>`
   - Ussage: `[optional]: <class name>.all()`
 - `update`: Updates an instance based on the class name and id by adding or          updating attribute. (save the change into the JSON file).
   - Ussage: `update <class name> <id> <attribute name> '<attribute value>'`
 - `quit`: Exit the console.
   - Ussage: `quit`
 - `EOF`: "Exit the console.
   - Ussage: `EOF`
   - Ussage: `[optional]: ctrl + D`

#### `models/` ---> Directory that contains main classes:

[base_model.py](/models/base_model.py): The class BaseModel is the main class that defines all common attributes/methods for other classes.

**Methods inside this class:**
 - `def __init__(self, *args, **kwargs)`: Constructor for BaseModel.
 - `def save(self)`: Saves current time to updated_at attribute.
 - `def to_dict(self)`: Return a dicctionary all the attributres keys/values.
 - `def __str__(self)`: return readable object with format `[<class name>] (<self.id>) <self.__dict__`.

**Classes inherited from Base Model:**
 - [amenity.py](/models/amenity.py): Creates Amenity intances.
   - Public class attributes:
		- **name**: string - empty string
 - [city.py](/models/city.py): Creates City intances.
   - Public class attributes:
		- **state_id**: string - empty string: it will be the State.id
		- **name**: string - empty string
 - [place.py](/models/place.py): Creates Place intances.
   - **city_id:** string - empty string: it will be the City.id
		- **user_id:** string - empty string: it will be the User.id
		- **name:** string - empty string
		- **description:** string - empty string
		- **number_rooms:** integer - 0
		- **number_bathrooms:** integer - 0
		- **max_guest:** integer - 0
		- **price_by_night:** integer - 0
		- **latitude**: float - 0.0
		- **longitude**: float - 0.0
		- **amenity_ids**: list of string - empty list: it will be the list of Amenity.id later
 - [review.py](/models/review.py): Creates Review intances.
   - Public class attributes:
		- **place_id:** string - empty string: it will be the Place.id
		- **user_id:** string - empty string: it will be the User.id
		- **text:** string - empty string
 - [state.py](/models/state.py): Creates State intances.
   - Public class attributes:
   		- **name:** will be the name of teh state to
 - [user.py](/models/user.py): Creates User intances.

#### `/models/engine` ---> Directory that contains File Storage class that manages JSON serialization and deserialization:
[file_storage.py](/models/engine/file_storage.py): The class FileStorage serializes instances to a JSON file and deserializes JSON file to instances.
 - `def all(self)`: Returns the dictionary __objects
 - `def new(self, obj)`: Sets in __objects the obj with key <obj class name>.id
 - `def save(self)`: Serializes __objects to the JSON file (path: __file_path)
 - ` def reload(self)`: Deserializes the JSON file to __objects

#### `/tests` ---> Directory contains all unit test cases for this project:
[/test_models/test_base_model.py](/tests/test_models/test_base_model.py): Contains the TestBaseModel and TestBaseModelDocs classes

------------

## Examples

------------

------------

## Bugs
There was not found bugs, if you find one, contact to the Authors.


------------
## Authors
Carlso Andres Ariztisabal - [Github](https://github.com/aristizabaru) / [Twitter](https://twitter.com/aristizabaru)  
Carlos Alberto Usuga Martinez - [Github](https://github.com/klich1984) / [Twitter](https://twitter.com/usuga_martinez)

------------
## License
Public Domain. No copy write protection.