.. _reference-editors-sublime_text-instalacion_packages:

####################
Instalacion Packages
####################

Instalacion de Package Control
******************************

.. code-block:: python

    import urllib.request,os,hashlib; h = '7183a2d3e96f11eeadd761d777e62404' + 'e330c659d4bb41d3bdf022e94cab3cd0'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

Packages comunes
****************

* SublimeLinter
* DocBlockr
* Git
* SideBarGit
* GitGutter
* SidebarEnhancements
* Tabright
* BlockCursorEverywhere (https://github.com/jlangston/BlockCursorEverywhere)

Theme
*****

* Predawn

Python
******

* Anaconda
* Djaneiro
* Python Imports Sorter

Python varios
=============

* SublimeREPL
* PythonImproved

Javascript Css
==============

Requiere algunos paquetes de :ref:`reference-linux-instalacion_nodejs`

* less
* less2css
* Better Typescript
* Minifier (ctrl + alt + shift + m)

Otros
*****

Me dejo aquí algunos addons para recordar el nombre.

* Theme - Flatland
* SublimeLinter-pep8
* Monokai extended
* AllAutocomplete
* SublimeCodeIntel
* Markdown Preview
* Alignment
* Emmet
* PHP Getters and Setters
* php-twig
* FavoriteFiles
* Tomorrow Color Schemes
* Theme - Soda
* Theme - Spacegray
* Theme - Spacefunk
