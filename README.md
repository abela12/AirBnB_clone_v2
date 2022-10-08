# AirBnB Clone (HBNB)

[![CodeStyle](https://github.com/B3zaleel/AirBnB_clone_v2/actions/workflows/codestyle.yml/badge.svg)](https://github.com/B3zaleel/AirBnB_clone_v2/actions/workflows/codestyle.yml)
![Latest commit](https://img.shields.io/github/last-commit/B3zaleel/AirBnB_clone_v2/master?style=round-square)

## Description

This repository contains the initial stage of a student project to build a clone of the AirBnB website. This stage implements a backend interface, or console, to manage program data. Console commands allow the user to create, update, and destroy objects, as well as manage file storage. Using a system of JSON serialization/deserialization, storage is persistent between sessions.

---


## The Command Interpreter

The command interpreter provides a simple REPL (Read-Evaluate-Print-Loop) for interacting with the models in this project only. It can be used to test the functionality of the supported storage engines as well. You can find some examples of its usage [here](#examples).

### How To Use

1. First clone this repository.

2. Once the repository is cloned locate the "[console.py](console.py)" file and run it as follows:
   ```powershell
   ➜  AirBnB_clone_v2 git:(master) ✗ ./console.py
   ```

4. When this command is run the following prompt should appear:
   ```
   (hbnb)
   ```

5. This prompt designates that you are in the "HBnB" console. There are a variety of commands available within the console program.

### Supported Commands

These are commands that can be executed by the command interpreter. They have the format `command [argument]...` but you could also use the format `Model.command([argument]...)`, with the exception of the first 3 commands below.

| Format | Description |
|:-|:-|
| `help [command]` | Prints helpful information about a command (`command`). If `command` is not provided, it prints the help menu. |
| `quit` | Closes the command interpreter. |
| `EOF` | Closes the command interpreter. |
| `create Model [prop_key=prop_value]...` | Creates a new instance of the `Model` class with the given properties. `prop_value` can be a double-quoted string with double-quotes escaped and spaces replaced with underscores. `prop_value` can also be a float or integer. |
| `count Model` | Prints the number of instances of the `Model` class. |
| `show Model id` | Prints the string representation of an instance of the `Model` class with the given `id`. |
| `destroy Model id` | Deletes an instance of the `Model` class with the given `id`. |
| `all [Model]` | Prints a list containing the string representation of all instances of the `Model` class. `Model` is optional and if it isn't provided, all the availble objects are printed. |
| `update Model id attr_name attr_value` | Updates an instance of the `Model` class with the given `id` by assigning the attribute value `attr_value` to its attribute named `attr_name`. Attributes having the names `__class__`, `id`, `created_at`, and `updated_at` are silently ignored. |
| `update Model id dict_repr` | Updates an instance of `Model` having the given `id` by storing the key, value pairs in the given `dict_repr` dictionary as its attributes. The keys `__class__`, `id`, `created_at`, and `updated_at` are silently ignored. |
<br>

### Supported Models

These are the models that are currently available.

| Class | Description |
|:-|:-|
| BaseModel | A(n abstract) class that represents the base class for all models (all models are instances of this class). |
| User | Represents a user account. |
| State | Represents the geographical state in which a _User_ lives or a _City_ belongs to. |
| City | Represents an urban area in a _State_. |
| Amenity | Represents a useful feature of a _Place_. |
| Place | Represents a building containing rooms that can be rented by a _User_. |
| Review | Represents a review of a _Place_. |

### Environment Variables

+ `HBNB_ENV`: The running environment. It can be `dev` or `test`.
+ `HBNB_MYSQL_USER`: The MySQL server username.
+ `HBNB_MYSQL_PWD`: The MySQL server password.
+ `HBNB_MYSQL_HOST`: The MySQL server hostname.
+ `HBNB_MYSQL_DB`: The MySQL server database name.
+ `HBNB_TYPE_STORAGE`: The type of storage used. It can be `file` (using `FileStorage`) or `db` (using `DBStorage`).

### Examples

<h3>Primary Command Syntax</h3>

###### Example 0: Create an object
Usage: create <class_name>
```
(hbnb) create BaseModel
```
```
(hbnb) create BaseModel
3aa5babc-efb6-4041-bfe9-3cc9727588f8
(hbnb)
```

###### Example 1: Show an object
Usage: show <class_name> <_id>

```
(hbnb) show BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
[BaseModel] (3aa5babc-efb6-4041-bfe9-3cc9727588f8) {'id': '3aa5babc-efb6-4041-bfe9-3cc9727588f8', 'created_at': datetime.datetime(2020, 2, 18, 14, 21, 12, 96959),
'updated_at': datetime.datetime(2020, 2, 18, 14, 21, 12, 96971)}
(hbnb)
```

###### Example 2: Destroy an object

Usage: destroy <class_name> <_id>
```
(hbnb) destroy BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
(hbnb) show BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
** no instance found **
(hbnb)
```
###### Example 3: Update an object
Usage: update <class_name> <_id>
```
(hbnb) update BaseModel b405fc64-9724-498f-b405-e4071c3d857f first_name "person"
(hbnb) show BaseModel b405fc64-9724-498f-b405-e4071c3d857f
[BaseModel] (b405fc64-9724-498f-b405-e4071c3d857f) {'id': 'b405fc64-9724-498f-b405-e4071c3d857f', 'created_at': datetime.datetime(2020, 2, 18, 14, 33, 45, 729889),
'updated_at': datetime.datetime(2020, 2, 18, 14, 33, 45, 729907), 'first_name': 'person'}
(hbnb)
```
<h3>Alternative Syntax</h3>

###### Example 0: Show all User objects
Usage: <class_name>.all()
```
(hbnb) User.all()
["[User] (99f45908-1d17-46d1-9dd2-b7571128115b) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 34, 92071), 'id': '99f45908-1d17-46d1-9dd2-b7571128115b', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 34, 92056)}", "[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```

###### Example 1: Destroy a User
Usage: <class_name>.destroy(<_id>)
```
(hbnb) User.destroy("99f45908-1d17-46d1-9dd2-b7571128115b")
(hbnb)
(hbnb) User.all()
(hbnb) ["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```
###### Example 2: Update User (by attribute)
Usage: <class_name>.update(<_id>, <attribute_name>, <attribute_value>)
```
(hbnb) User.update("98bea5de-9cb0-4d78-8a9d-c4de03521c30", name "Todd the Toad")
(hbnb)
(hbnb) User.all()
(hbnb) ["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'name': 'Todd the Toad', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```
###### Example 3: Update User (by dictionary)
Usage: <class_name>.update(<_id>, <dictionary>)
```
(hbnb) User.update("98bea5de-9cb0-4d78-8a9d-c4de03521c30", {'name': 'Fred the Frog', 'age': 9})
(hbnb)
(hbnb) User.all()
(hbnb) ["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'name': 'Fred the Frog', 'age': 9, 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
```
<br>

<!-- ## Testing -->

**NOTE:** Before you push any commit, please run the script `./test.bash` to ensure that no tests are failing and your code complies with this project's styling standard.
