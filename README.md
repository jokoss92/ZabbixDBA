## ZabbixDBA
Perl plugin for Zabbix to monitor RDBMS. Used Orabbix as example.  
  
ZabbixDBA uses threading of DBI connections which is good for monitoring of multiple database instances.
Currently there are template and query set only for Oracle database, but Perl DBI supports any type of RDBMS:
- MySQL
- MS SQL
- PostgreSQL
- DB2
  
You can find full list of DBD modules here: https://metacpan.org/search?q=DBD
  
Feel free to fork and contribute!
  
#### Installation
Put the script **init.d/ZabbixDBA** to your **/etc/init.d** directory
```
cp init.d/ZabbixDBA /etc/init.d
chmod +x /etc/init.d/ZabbixDBA
/sbin/chkconfig ZabbixDBA on     # enable automatic startup/shutdown
```
  
To install all Perl requirements execute the following in plugin directory:
```
cpanm --installdeps .
```
  
#### Usage
```
/sbin/service ZabbixDBA {start|stop|restart|reload|status}
```
  
#### Configuration
Create user ZABBIX (or whatever you want) in database and grant privileges regarding your privacy policy.  
Add your database information just like described in **conf/config.pl** (this file uses Perl hash structure to describe configuration).

#### Features

- [Discovery rules](docs/DiscoveryRules.md)
- [send_to](docs/SendTo.md)
  
#### TODO
- reformat code for easy reading and maintenance
- ~~add start/stop scripts~~
- ~~add comments~~
- ~~add logging~~
- ~~add SIG signal handlers to stop loop gracefully~~
- ~~add Zabbix template~~
- ~~add ability to create discovery rules~~
