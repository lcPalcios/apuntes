.. _reference-editors-sublime_text-anaconda:

########
Anaconda
########

**Fuentes**

* https://github.com/DamnWidget/anaconda/blob/master/Anaconda.sublime-settings

----

La configuracion se pone en
``Preferences -> Package Settings -> Anaconda -> Settings - User``

.. code-block:: javascript

    {
        "python_interpreter": "/home/snicoper/Desktop/test/venv/bin/python3",
        "anaconda_linter_mark_style": "none",
        "complete_parameters": true,
        "anaconda_gutter_theme": "alpha",
        "display_signatures": true,
        "pep8_max_line_length": 100,
        "auto_formatting": false,
        "pep8_ignore":
        [
            "E309",
        ],
    }
