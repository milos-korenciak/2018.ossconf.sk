PyCon SK 2018 Website
#####################

.. image:: https://preklady.python.sk/widgets/pycon-sk-2018-website/sk/github/svg-badge.svg?native=1
    :alt: Translation status
    :target: https://preklady.python.sk/engage/pycon-sk-2018-website/sk/?utm_source=widget


Official `PyCon SK 2018 <https://2018.pycon.sk/>`_ website.


Contributing
------------

Contributions are welcome. If you found a bug please open an issue at our GitHub repo, or submit a pull request. We do welcome any kind of pull request event if it is just a typo ;)


Project structure
-----------------

**1 branch**:

- ``master`` - the `Flask <http://flask.pocoo.org/>`_ app, templates, static files, translations (make your changes here)


Installation
------------

- clone repository locally::

    git clone https://github.com/pyconsk/2018.pycon.sk.git
    cd 2018.pycon.sk

- creates a virtual environment, activate it and installs all requirements::

    pyvenv envs3
    source envs3/bin/activate
    pip install -r requirements.txt --no-use-wheel

- start flask server, and you can view it in browser (http://127.0.0.1:5000/en/index.html)::

    python views.py


Translations
------------

Translations are made with `Flask-Babel <https://pythonhosted.org/Flask-Babel/>`_. All translations are located in ``translations`` directory, update ``messages.po`` with your translations messages.

- collect translation strings from Flask app::

    pybabel extract -F babel.cfg -o messages.pot .

- update translation ``messages.po`` files with collected translation strings::

    pybabel update -i messages.pot -d translations

- compile translated messages and generate ``messages.po`` files::

    pybabel compile -d translations


Generate static site
--------------------

`Frozen-Flask <https://pythonhosted.org/Frozen-Flask/>`_ freezes a Flask application into a set of static files. The result can be hosted without any server-side software other than a traditional web server.

- generate static files, and you can find them in ``build`` directory::

    python freezer.py

- verify the generated result in browser (http://127.0.0.1:8000/en/index.html)::

    cd build
    python -m SimpleHTTPServer 8000


Continuous Deployment
---------------------

Anything committed to master branch will be automatically deployed on live server. Live site contain only generated static site in ``build`` directory.


Fonts
-----

Embedded pyconsk font generated with `Fontello <http://fontello.com>`_ and contain `Font Awesome <http://fontawesome.io/>`_ and `Entypo <http://www.entypo.com>`_ icons.


Stylesheets
-----------

For grids and base layout we use `Picnic CSS <https://picnicss.com/>`_, our design is stored in pyconsk.css stylesheet. Both files are merged and minimized via `YUI Compressor <https://yui.github.io/yuicompressor/>`_::

    cat picnic.css pyconsk.css > stylesheet.css
    java -jar yuicompressor.jar stylesheet.css -o stylesheet.min.css


Links
-----

- web: https://2018.pycon.sk
- facebook: https://facebook.com/pyconsk
- twitter: https://twitter.com/pyconsk


License
-------

* MIT license for code (code - GitHub repo)
* CC-BY for content, except sponsors logo's (consult with particular company if you would like to use their logo)
* SIL for embedded fonts

For more details read the LICENSE file.
