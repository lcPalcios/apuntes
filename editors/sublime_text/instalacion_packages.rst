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
* Monokai extended
* SidebarEnhancements
* Tabright

Theme
*****

* Theme - Soda
* Tomorrow Color Schemes

Python
******

* Anaconda
* Djaneiro

Python varios
=============

* SublimeREPL
* PythonImproved

Otros
*****

* AllAutocomplete
* SublimeCodeIntel
* Markdown Preview
* Alignment
* Emmet
* PHP Getters and Setters
* php-twig
* FavoriteFiles
* TypeScript
* TypeScript Compiler
