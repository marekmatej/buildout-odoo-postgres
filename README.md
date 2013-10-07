Buildout for OpenERP with PostgreSQL
====================================

Buildout for OpenERP 7.0, PostgreSQL 9.3 and Supervisord

Usage
=====
```Shell
cd virtualenv projects dir
git clone https://github.com/kybi/buildout-openerp-postgres openerp
mkvirtualenv openerp
cdvirtualenv
mkdir eggs
python bootstrap.py
buildout
```