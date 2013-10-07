Buildout for OpenERP with PostgreSQL
====================================

OpenERP 7.0, PostgreSQL 9.3 and Supervisord 3.0

Usage
=====
```Shell
cd virtualenv projects dir
git clone https://github.com/kybi/buildout-openerp-postgres openerp
mkvirtualenv openerp
cdvirtualenv
mkdir eggs
python bootstrap.py
change settings in buildout.cfg
buildout
supervisord             # start supervisor deamon
supervisorctl status    # check if running postgres
psql -d postgres -c 'CREATE DATABASE ...'  # copy this line from shell after run buildout
start_openerp
```

Settings
=========

default in buildout.cfg, change values before run buildout

```Shell
openerp_version = nightly 7.0 latest

postgres_version = 9.3.0
postgres_host = 127.0.0.1
postgres_db_name = openerp
postgres_port = 5434
postgres_maxconn = 100

supervisor_port = 9002
supervisor_url = http://127.0.0.1
```