Introduction
============

This is a buildout to create a LAMP stack.

For more information, please see:

+   http://blog.aclark.net/2010/07/12/the-apache-modules-for-xdv/

References
==========

Buildout:

+   http://buildout.org

LAMP Stack:

+   http://en.wikipedia.org/wiki/LAMP_(software_bundle)

Dependencies
============

::

    sudo apt-get install \
        cmake libncurses5-dev cmake-curses-gui libpng12-dev \
        libmcrypt-dev \
        libgd2-xpm-dev # – because php compilation fails…

Install
=======

To install, do the following::

    $ git clone git://github.com/vakaras/lamp-buildout.git lamp
    $ cd lamp
    $ make

Go get coffee, then::

    $ chmod 755 ${HOME}/.buildout/eggs/supervisor-3.0a12-py2.7.egg/supervisor/pidproxy.py
    $ bin/supervisord -e debug -n
    $ bin/mysqladmin -u root password 'new-password'

Now go to http://localhost:9002 and try to log on. Then, if everything looks good::

    $ bin/supervisord

Configure
=========

You can change the default ports by editing buildout.cfg::

    [ports]
    …
    supervisor = 9001
    apache = 8080
    mysql = 3306

Then rerun buildout::

    $ bin/buildout

Virtual Hosting
===============

You can run numerous, isolated PHP environments by proxying
from a web server running on port 80 to the buildout's 
Apache. If you are using Apache on port 80, this can be done 
with mod_proxy_html:

+   http://apache.webthing.com/mod_proxy_html/


Credits
=======

Author: Alex Clark <aclark@aclark.net>
