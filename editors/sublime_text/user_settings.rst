.. _reference-editors-sublime_text-user_settings:

#############
Settings User
#############

Esta configuración la uso tanto en Linux como en Windows, solo mirar que
la fuente este instalada o cambiar por otra, también ajustar tamaño fuente.

Abrir Preferences > Setting - User

.. code-block:: javascript

    {
        // Colors and theme
        "theme": "predawn.sublime-theme",
        "color_scheme": "Packages/Predawn/predawn.tmTheme",
        "tabs_small": true,
        "findreplace_small": true,

        // Font
        "font_face": "Source Code Pro",
        "font_size": 10.5,
        "font_options": "subpixel_antialias",

        // Editor view look-and-feel
        "highlight_line": true,
        "show_minimap": false,
        "show_full_path": true,
        "bold_folder_labels": true,

        // Editor behavior
        "highlight_modified_tabs": true,
        "find_selected_text": true,
        "shift_tab_unindent" : false,
        "tab_completion": false,

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
            "migrations",
        ],
        "ignored_packages":
        [
        ],
        "vintage_start_in_command_mode": true
    }
