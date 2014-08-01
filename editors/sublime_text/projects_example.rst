.. _reference-editors-sublime_text-projects_example:

#####################
Ejeplo de un Proyecto
#####################

Referencia de un archivo de proyecto ``Sublime Text 3``

.. code-block:: javascript

    {
        "folders":
        [
            {
                "follow_symlinks": true,
                "path": "/home/snicoper/projects/python",
                "folder_exclude_patterns": [
                    ".idea",
                ],
                "file_exclude_patterns": [
                    "phpdoc-*",
                    ".directory",
                ]
            }
        ],
        // Anaconda
        "settings": {
            "python_interpreter": "/home/snicoper/.virtualenvs/py3venv/bin/python3",
             "auto_complete_triggers": [
                {"selector": "source.python - string - comment - constant.numeric",
                "characters": "."}]
        }
    }
