floep takes a simple configuration file with hosts and groups of hosts (or groups of groups), and allows you to execute commands on a group of servers in parallel.

# Configuration #

```
[settings]
defaultGroup=all
commandTemplate=ssh %(host)s %(command)s 

[all]
group=www,db

[www]
group=www1,www2

[db]
group=db1,db2

[www1]
host=www1

[www2]
host=www2

[db1]
host=db1

[db2]
host=db2
```

This file needs to be in floep.cfg. Floep looks for this file in the same directory as the script, and the current directory. If both exist, it will load both in this order.

# Using it #

```
$ ./floep uptime
floep 0.1
Result from www1 :
 13:27:57 up 36 days, 15:07,  0 users,  load average: 0.05, 0.04, 0.01

Result from www2 :
 13:27:57 up 17 days, 21:39,  0 users,  load average: 0.04, 0.04, 0.00

Result from db2 :
 13:27:57 up 36 days, 15:07,  0 users,  load average: 0.31, 0.33, 0.39

Result from db1 :
 13:27:57 up 36 days, 15:07,  1 user,  load average: 0.04, 0.10, 0.08
```

Also check ./floep -h
