# firefly-container
A standalone firefly iii container.

FF
## Setup

```
FFDB_PATH="/mnt/volumes/container/ffdb"
FFDB_FILE="firefly.sql"
if [ ! -f "$FFDB_PATH/$FFDB_FILE" ] ; then 
 /bin/mkidr -p $FFDB_PATH/
 /bin/touch $FFDB_PATH/$FFDB_FILE
 cd /opt/firefly
 /usr/bin/php artisan firefly-iii:upgrade-database 
 /usr/bin/php artisan firefly-iii:correct-database
 /usr/bin/php artisan firefly-iii:report-integrity
 /usr/bin/php artisan passport:install --force
 /bin/chown firefly:www-data -R $FFDB_PATH
 /bin/chmod 777 -R $FFDB_PATH
fi
 ```


https://github.com/orgs/firefly-iii/discussions/4991




