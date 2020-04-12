# Oracle Database

## SQL Client

Oracle SQL client will not timeout if connection fails because of incorrect hostname, unless SQLNET.OUTBOUND_CONNECT_TIMEOUT is set in sqlnet.ora and the TNS_ADMIN variable is set in php-fpm config pointing to the sqlnet.ora directory.
