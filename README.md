# Buildout for OpenERP with PostgreSQL
OpenERP 7.0, PostgreSQL 9.3 and Supervisord 3.0
- Buildout create cron for starting Supervisord after machine reboot
- Supervisor run PostgreSQL, more http://supervisord.org/
- PostgreSQL run under user, and build enabled "trust" authentication for local connections,
 more http://www.postgresql.org/docs/9.3/static/auth-methods.html

# Usage
```
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

# Settings
defaults in buildout.cfg

```
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
## OpenERP
config file: etc/openerp.cfg, if you want change more options in openerp.cfg, don't edit this file,
please add section [openerp] to buildout.cfg
and set options.'add_option' = value, where 'add_option' is from openerp.cfg and run buildout again.

Example: change logging level
```
...
[openerp]
options.log_handler = [':ERROR']
...
```

if you want running more then one instance of OpenERP, or another user running same buildout,
please change ports:
```
openerp_xmlrpc_port = 8069  (8069 default openerp)
openerp_xmlrpcs_port = 8071 (8071 default openerp)
supervisor_port = 9002      (9001 default supervisord)
postgres_port = 5434        (5432 default postgres)
```

# TODO
- move Usage to Fabric, more http://fabfile.org/
- generate Apache and Nginx config for virualhost with Buildout

# Contributors

## Creators

Rastislav Kober, http://www.kybi.sk