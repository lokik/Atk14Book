Requirements
============

### Apache webserver

You need one to be installed :)

	$ sudo apt-get install apache2-mpm-prefork

Mod Rewrite has to be enabled.

	$ cd /etc/apache2/mods-enabled/
	$ sudo ln -s ../mods-available/rewrite.load ./

### Git

You need Git to checkout ATK14 source codes from <https://github.com/yarri/Atk14>

	$ sudo apt-get install git

### PHP

	$ sudo apt-get install php5 php5-cli

### Postgresql

You need Postgresql server to be installed on you system. Install also the postgresql PHP extension.

	$ sudo apt-get install postgresql php5-pgsql

Postgresql access control file pg\_hba.conf should look like this. The file may be found at /etc/postgresql/8.4/main/pg\_hba.conf

	# TYPE  DATABASE    USER       CIDR-ADDRESS  METHOD
	local   all         postgres                 ident
	host    all         postgres   127.0.0.1/32  ident
	host    all         postgres   ::1/128       ident
	local   sameuser    all                      md5
	host    sameuser    all        127.0.0.1/32  md5
	host    sameuser    all        ::1/128       md5

These lines say that administer (postgres) can connect to any database but only when he is logged as postgres in the system, other user can connect only to a database with the same name and must provide a correct password.

Now restart the server.

	$ sudo service postgresql restart
	or
	$ sudo /etc/init.d/postgresql restart

### Gettext

If you are planning to develop a multilanguage application, you need Gettext to be installed.

	$ sudo apt-get install gettext php-gettext

Great tool for edition *.po files is Poedit.

	$ sudo apt-get install poedit

Be sure that /var/lib/locales/supported.d/local contains lines:

	en_US.UTF-8 UTF-8
	cs_CZ.UTF-8 UTF-8

If it doesn't add these locales and then run:

	$ sudo locale-gen

