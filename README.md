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
openerp_xmlrpc_port = 8069
openerp_xmlrpcs_port = 8071

postgres_version = 9.3.0
postgres_host = 127.0.0.1
postgres_db_name = openerp
postgres_port = 5434
postgres_maxconn = 100

supervisor_port = 9002
supervisor_url = http://127.0.0.1
```

if you want running more then one instance of openerp, or another user running same buildout,
please change ports:
```Shell
openerp_xmlrpc_port = 8069  (8069 default openerp)
openerp_xmlrpcs_port = 8071 (8071 default openerp)
supervisor_port = 9002      (9001 default supervisord)
postgres_port = 5434        (5432 default postgres)
```

TODO
====

- move Usage to fabric
- generate apache and nginx config for virualhost with buildout