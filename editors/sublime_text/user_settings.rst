.. _reference-editors-sublime_text-user_settings:

#############
Settings User
#############

Esta configuracion la uso tanto en linux como en windows, solo mirar que
la fuente este instalada o cambiar por otra, tambien ajustar tamaño fuente.

Abrir Preferences > Setting - User

.. code-block:: javascript

    {
        // Colors
        "theme": "Flatland Dark.sublime-theme",
        "color_scheme": "Packages/Theme - Flatland/Flatland Dark.tmTheme",

        // Font
        "font_face": "Ubuntu Mono",
        "font_size": 10.5,
        "font_options": ["subpixel_antialias"],

        // Editor view look-and-feel
        "highlight_line": true,
        "show_minimap": false,
        "show_full_path": true,

        // Editor behavior
        "highlight_modified_tabs": true,
        "find_selected_text": true,
        "shift_tab_unindent" : true,

        // Word wrapping - follow PEP 8 recommendations
        "rulers": [ 100 ],
        "word_wrap": false,

        // Whitespace - no tabs, trimming, end files with \n
        "tab_size": 4,
        "translate_tabs_to_spaces": true,
        "trim_trailing_white_space_on_save": true,
        "ensure_newline_at_eof_on_save": true,

        // Sidebar - exclude distracting files and folders
        "file_exclude_patterns":
        [
            ".DS_Store",
            "*.pid",
            "*.pyc",
            ".directory",
            "*.sublime*",
        ],
        "folder_exclude_patterns":
        [
            ".git",
            ".svn",
            ".hg",
            "__pycache__",
            "env",
            "env3",
            ".idea",
            ".codeintel",
        ],
        "ignored_packages":
        [
            //"Vintage"
        ]
    }

