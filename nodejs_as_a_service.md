# Install nodejs as a service #

*Attention: You must have the nodejs installed with the nodejs user, as you can see in [Installing nodejs on centos](nodejs)*


Easy-peasy, first create this script (it's for bombur-server, but you can change it easily):


```
#!bash

sudo nano /etc/init.d/bombur_server
```

```
#!/bin/sh

#
# chkconfig: 35 99 99
# description: Node.js /var/www/nodejs/bombur-server
#

. /etc/rc.d/init.d/functions

USER="nodejs"

DAEMON="/home/nodejs/.local/bin/node"
ROOT_DIR="/var/www/nodejs/bombur-server"

SERVER="$ROOT_DIR/server.js"
LOG_FILE="$ROOT_DIR/server.js.log"

LOCK_FILE="/var/lock/subsys/node-server"
 
do_start()
{
        if [ ! -f "$LOCK_FILE" ] ; then
                echo -n $"Starting $SERVER: "
                runuser -l "$USER" -c "$DAEMON $SERVER >> $LOG_FILE &" && echo_success || echo_failure
                RETVAL=$?
                echo
                [ $RETVAL -eq 0 ] && touch $LOCK_FILE
        else
                echo "$SERVER is locked."
                RETVAL=1
        fi
}
do_stop()
{
        echo -n $"Stopping $SERVER: "
        pid=`ps -aefw | grep "$DAEMON $SERVER" | grep -v " grep " | awk '{print $2}'`
        kill -9 $pid > /dev/null 2>&1 && echo_success || echo_failure
        RETVAL=$?
        echo
        [ $RETVAL -eq 0 ] && rm -f $LOCK_FILE
}
 
case "$1" in
        start)
                do_start
                ;;
        stop)
                do_stop
                ;;
        restart)
                do_stop
                do_start
                ;;
        *)
                echo "Usage: $0 {start|stop|restart}"
                RETVAL=1
esac
 
exit $RETVAL


```

And then you have your own service. Something like:


```
#!bash

sudo service start bombur_server

#or 

sudo service stop bombur_server
```

