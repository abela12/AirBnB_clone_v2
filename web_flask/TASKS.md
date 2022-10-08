# Tasks To Complete

+ [x] 0. Hello Flask!<br/>_**[0-hello_route.py](0-hello_route.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  + Routes:
    + `/`: display "Hello HBNB!".
  + You must use the option `strict_slashes=False` in your route definition.

+ [x] 1. HBNB<br/>_**[1-hbnb_route.py](1-hbnb_route.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  + Routes:
    + `/`: display "Hello HBNB!".
    + `/hbnb`: display "HBNB".
  + You must use the option `strict_slashes=False` in your route definition.

+ [x] 2. C is fun!<br/>_**[2-c_route.py](2-c_route.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  + Routes:
    + `/`: display "Hello HBNB!".
    + `/hbnb`: display "HBNB".
    + `/c/<text>`: display "C " followed by the value of the `text` variable (replace underscore `_` symbols with a space ` `).
  + You must use the option `strict_slashes=False` in your route definition.

+ [x] 3. Python is cool!<br/>_**[3-python_route.py](3-python_route.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  + Routes:
    + `/`: display "Hello HBNB!".
    + `/hbnb`: display "HBNB".
    + `/c/<text>`: display "C ", followed by the value of the `text` variable (replace underscore _ symbols with a space ` `).
    + `/python/(<text>)`: display "Python ", followed by the value of the `text` variable (replace underscore `_` symbols with a space ` `).
      + The default value of `text` is "is cool".
  + You must use the option `strict_slashes=False` in your route definition.

+ [x] 4. Is it a number?<br/>_**[4-number_route.py](4-number_route.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  + Routes:
    + `/`: display "Hello HBNB!".
    + `/hbnb`: display "HBNB".
    + /c/<text>: display "C ", followed by the value of the `text` variable (replace underscore `_` symbols with a space ` `).
    + `/python/(<text>)`: display "Python ", followed by the value of the `text` variable (replace underscore `_` symbols with a space ` `).
      + The default value of `text` is "is cool".
    + `/number/<n>`: display "`n` is a number" **only** if `n` is an integer.
  + You must use the option `strict_slashes=False` in your route definition.

+ [x] 5. Number template<br/>_**[5-number_template.py](5-number_template.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  + Routes:
    + `/`: display "Hello HBNB!".
    + `/hbnb`: display "HBNB".
    + `/c/<text>`: display "C ", followed by the value of the `text` variable (replace underscore `_` symbols with a space ` `).
    + `/python/(<text>)`: display "Python ", followed by the value of the `text` variable (replace underscore `_` symbols with a space ` `).
      + The default value of `text` is "is cool".
    + `/number/<n>`: display "`n` is a number" **only** if `n` is an integer.
    + `/number_template/<n>`: display a HTML page **only** if `n` is an integer:
      + [templates/5-number.html](templates/5-number.html) contains the template.
      + `H1` tag: "Number: `n`" inside the tag `BODY`.
  + You must use the option `strict_slashes=False` in your route definition.

+ [x] 6. Odd or even?<br/>_**[6-number_odd_or_even.py](6-number_odd_or_even.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  + Routes:
    + `/`: display "Hello HBNB!".
    + `/hbnb`: display "HBNB".
    + `/c/<text>`: display "C ", followed by the value of the `text` variable (replace underscore `_` symbols with a space ` `).
    + `/python/(<text>)`: display "Python ", followed by the value of the `text` variable (replace underscore `_` symbols with a space ` `).
      + The default value of `text` is "is cool".
    + `/number/<n>`: display "`n` is a number" **only** if `n` is an integer.
    + `/number_template/<n>`: display a HTML page **only** if n is an integer:
      + [templates/5-number.html](templates/5-number.html) contains the template.
      + `H1` tag: "Number: `n`" inside the tag `BODY`.
    + `/number_odd_or_even/<n>`: display a HTML page **only** if `n` is an integer:
      + [templates/6-number_odd_or_even.html](templates/6-number_odd_or_even.html) contains the template.
      + `H1` tag: "Number: `n` is even|odd" inside the tag `BODY`.
  + You must use the option `strict_slashes=False` in your route definition.

+ [x] 7. Improve engines
  + **INFO**: Before using Flask to display our HBNB data, you will need to update some part of our engine.
  + Update [`FileStorage`](../models/engine/file_storage.py):
    + Add a public method `def close(self):`: call `reload()` method for deserializing the JSON file to objects.
  + Update [`DBStorage`](../models/engine/db_storage.py):
    + Add a public method `def close(self):`: call `remove()` method on the private session attribute (`self.__session`) [tips](https://docs.sqlalchemy.org/en/13/orm/contextual.html) or `close()` on the class `Session` [tips](https://docs.sqlalchemy.org/en/13/orm/session_api.html).
  + Update [`State`](../models/state.py) - If it's not already present.
    + If your storage engine is not `DBStorage`, add a public getter method `cities` to return the list of `City` objects from storage linked to the current `State`.

+ [x] 8. List of states<br/>_**[7-states_list.py](7-states_list.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  + You must use `storage` for fetching data from the storage engine (`FileStorage` or `DBStorage`) => `from models import storage` and `storage.all(...)`.
  + After each request you must remove the current SQLAlchemy Session:
    + Declare a method to handle `@app.teardown_appcontext`.
    + Call in this method `storage.close()`.
  + Routes:
    + `/states_list`: display a HTML page: (inside the tag `BODY`).
      + [templates/7-states_list.html](templates/7-states_list.html) contains the template.
      + `H1` tag: "States".
      + `UL` tag: with the list of all `State` objects present in `DBStorage` **sorted by `name`** (A->Z).
        + `LI` tag: description of one `State`: `<state.id>: <B><state.name></B>`.
  + Import this [dump](dump0.sql) to have some data.
  + You must use the option `strict_slashes=False` in your route definition.
  + **IMPORTANT**
    + Make sure you have a running and valid [`setup_mysql_dev.sql`](../setup_mysql_dev.sql).
    + Make sure all tables are created when you run `echo "quit" | HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db ./console.py`.

+ [x] 9. Cities by states<br/>_**[8-cities_by_states.py](8-cities_by_states.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  + You must use `storage` for fetching data from the storage engine (`FileStorage` or `DBStorage`) => `from models import storage` and `storage.all(...)`.
  + To load all cities of a `State`:
    + If your storage engine is `DBStorage`, you must use `cities` relationship.
    + Otherwise, use the public getter method `cities`.
  + After each request you must remove the current SQLAlchemy Session:
    + Declare a method to handle `@app.teardown_appcontext`.
    + Call in this method `storage.close()`.
  + Routes:
    `/cities_by_states`: display a HTML page: (inside the tag `BODY`).
      + [templates/8-cities_by_states.html](templates/8-cities_by_states.html) contains the template.
      + `H1` tag: "States".
      + `UL` tag: with the list of all `State` objects present in `DBStorage` **sorted by `name`** (A->Z).
        + `LI` tag: description of one `State`: `<state.id>: <B><state.name></B>` + `UL` tag: with the list of `City` objects linked to the `State` **sorted by `name`** (A->Z).
          + `LI` tag: description of one `City`: `<city.id>: <B><city.name></B>`.
  + Import this [dump](dump0.sql) to have some data.
  + You must use the option `strict_slashes=False` in your route definition.
  + **IMPORTANT**
    + Make sure you have a running and valid [setup_mysql_dev.sql](../setup_mysql_dev.sql).
    + Make sure all tables are created when you run `echo "quit" | HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db ./console.py`.

+ [x] 10. States and State<br/>_**[9-states.py](9-states.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  You must use `storage` for fetching data from the storage engine (`FileStorage` or `DBStorage`) => `from models import storage` and `storage.all(...)`.
  To load all cities of a `State`:
    + If your storage engine is `DBStorage`, you must use `cities` relationship.
    + Otherwise, use the public getter method `cities`.
  + After each request you must remove the current SQLAlchemy Session:
    + Declare a method to handle `@app.teardown_appcontext`.
    + Call in this method `storage.close()`.
  + Routes:
    + `/states`: display a HTML page: (inside the tag `BODY`).
      + [templates/9-number_odd_or_even.html](templates/9-states.html) contains the template.
      + `H1` tag: "States".
      + `UL` tag: with the list of all `State` objects present in `DBStorage` **sorted by `name`** (A->Z).
        + `LI` tag: description of one `State`: `<state.id>: <B><state.name></B>`.
    + `/states/<id>`: display a HTML page: (inside the tag `BODY`).
      + [templates/9-states.html](templates/9-states.html) contains the template.
      + If a `State` object is found with this `id`:
        + `H1` tag: "State: ".
        + `H3` tag: "Cities:".
        + `UL` tag: with the list of `City` objects linked to the `State` **sorted by `name`** (A->Z).
          + `LI` tag: description of one `City`: `<city.id>: <B><city.name></B>`.
      + Otherwise:
        + `H1` tag: "Not found!".
  + You must use the option `strict_slashes=False` in your route definition.
  + Import this [dump](dump0.sql) to have some data.
  + **IMPORTANT**
    + Make sure you have a running and valid [setup_mysql_dev.sql](../setup_mysql_dev.sql).
    + Make sure all tables are created when you run `echo "quit" | HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db ./console.py`.

+ [x] 11. HBNB filters<br/>_**[10-hbnb_filters.py](10-hbnb_filters.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  + You must use `storage` for fetching data from the storage engine (`FileStorage` or `DBStorage`) => `from models import storage` and `storage.all(...)`.
  + To load all cities of a `State`:
    + If your storage engine is `DBStorage`, you must use `cities` relationship.
    + Otherwise, use the public getter method `cities`.
  + After each request you must remove the current SQLAlchemy Session:
    + Declare a method to handle `@app.teardown_appcontext`.
    + Call in this method `storage.close()`.
  + Routes:
    + `/hbnb_filters`: display a HTML page like [`6-index.html`](../web_static/6-index.html).
      + [templates/10-hbnb_filters.html](templates/10-hbnb_filters.html) contains the template.
      + Copy files [`3-footer.css`](../web_static/styles/3-footer.css), [`3-header.css`](../web_static/styles/3-header.css), [`4-common.css`](../web_static/styles/4-common.css), and [`6-filters.css`](../web_static/styles/6-filters.css) from `web_static/styles/` to the folder `web_flask/static/styles`.
      + Copy files [`icon.png`](../web_static/images/icon.ico) and [`logo.png`](../web_static/images/logo.png) from `web_static/images/` to the folder `web_flask/static/images`.
      + Update `.popover` class in [`6-filters.css`](static/styles/6-filters.css) to allow scrolling in the popover and a max height of 300 pixels.
      + Use [`6-index.html`](../web_static/6-index.html) content as source code for the template [`10-hbnb_filters.html`](templates/10-hbnb_filters.html):
        + Replace the content of the `H4` tag under each filter title (`H3` States and `H3` Amenities) by `&nbsp;`.
      + `State`, `City`, and `Amenity` objects must be loaded from `DBStorage` and **sorted by `name`** (A->Z).
  + You must use the option `strict_slashes=False` in your route definition.
  + Import this [dump](dump0.sql) to have some data.
  + **IMPORTANT**
    + Make sure you have a running and valid [setup_mysql_dev.sql](../setup_mysql_dev.sql).
    + Make sure all tables are created when you run `echo "quit" | HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db ./console.py`.

+ [x] 12. HBNB is alive!<br/>_**[100-hbnb.py](100-hbnb.py)**_ contains a script that starts a Flask web application.
  + Your web application must be listening on `0.0.0.0`, port `5000`.
  + You must use `storage` for fetching data from the storage engine (`FileStorage` or `DBStorage`) => `from models import storage` and `storage.all(...)`.
  + To load all cities of a `State`:
    + If your storage engine is `DBStorage`, you must use `cities` relationship.
    + Otherwise, use the public getter method `cities`.
  + After each request you must remove the current SQLAlchemy Session:
    + Declare a method to handle `@app.teardown_appcontext`.
    + Call in this method `storage.close()`.
  + Routes:
    + `/hbnb`: display a HTML page like [`8-index.html`](../web_static/8-index.html).
      + [templates/100-hbnb.html](templates/100-hbnb.html) contains the template.
      + Copy files [`3-footer.css`](../web_static/styles/3-footer.css), [`3-header.css`](../web_static/styles/3-header.css), [`4-common.css`](../web_static/styles/4-common.css), [`6-filters.css`](../web_static/styles/6-filters.css), and [`8-places.css`](../web_static/styles/8-places.css) from `web_static/styles/` to the folder `web_flask/static/styles`.
      + Copy all files from `web_static/images/` to the folder `web_flask/static/images`.
      + Update `.popover` class in [`6-filters.css`](static/styles/6-filters.css) to enable scrolling in the popover and set max height to 300 pixels.
      + Update [`8-places.css`](static/styles/8-places.css) to always have the price by night on the top right of each place element, and the name correctly aligned and visible (i.e. screenshots below).
      + Use [`8-index.html`](../web_static/8-index.html) content as source code for the template [`100-hbnb.html`](templates/100-hbnb.html):
        + Replace the content of the `H4` tag under each filter title (`H3` States and `H3` Amenities) by `&nbsp;`.
        + Make sure all HTML tags from objects are correctly used (example: `<BR />` must generate a new line).
      + `State`, `City`, `Amenity`, and `Place` objects must be loaded from `DBStorage` and sorted by name (A->Z).
  + You must use the option `strict_slashes=False` in your route definition.
  + Import this [dump](dump1.sql) to have some data.
  + **IMPORTANT**
    + Make sure you have a running and valid [setup_mysql_dev.sql](../setup_mysql_dev.sql).
    + Make sure all tables are created when you run `echo "quit" | HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db ./console.py`.
