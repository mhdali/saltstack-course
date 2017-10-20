## salt-master
Host that send actions called master, the master is a minion to itself.
![alt text](https://docs.saltstack.com/en/getstarted/images/master.png "salt-master")

## salt-minion
All hosts called minions, each minion has an ID (usually it's hostname).
![alt text](https://docs.saltstack.com/en/getstarted/images/minions.png "salt-minion")

## targeting
Initiate a commands on master giving a target to execute an action that  given by the master.

Usually target used by minion ID (Default minion hostname)
`salt '*' disk.usage`{{execute MASTER}}

![alt text](https://docs.saltstack.com/en/getstarted/images/remote-exe.png "remote-exe")

When minion connect to the master, there is an initial "handshake" process. (managed by salt-key)

The master and minions can communicate along a ZeroMQ data bus.

When the master publishes a command, it simply puts it on the ZeroMQ bus for all of the minions to see, each minion will then look at the command and the target to determine if it should run that command.


the central master can distribute files that describe how a system should be configured. called states, and they are stored in simple YAML files called SLS

```
webserver_main_index_file:
  file.managed:
    - name: /var/www/index.html
    - source: salt://webserver/main.html
```{{copy}}

the first line is the unique identifier, 2nd line is called state, 3rd and 4th are options of that state.

list of all available states in this URL [https://docs.saltstack.com/en/latest/ref/states/all/index.html](https://docs.saltstack.com/en/latest/ref/states/all/index.html)
