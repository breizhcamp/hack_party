# Our experiments on [RpiDocker](http://blog.docker.com/2015/09/update-raspberry-pi-dockercon-challenge/)

First run on a using base hypriot system took 2 minutes to run

On a RPi 1A (the _very_ old one), 53 containers start successfully, then:
```
Error response from daemon: Cannot start container 93eaa630a1dedd67501d4fc76d8cd6d0b76f08384791ac8670d94450b11ee19f: iptables failed: iptables --wait -t nat -A DOCKER -p tcp -d 0/0 --dport 10053 -j DNAT --to-destination 172.17.0.52:80 ! -i docker0:  (fork/exec /sbin/iptables: cannot allocate memory)
```
On a RPi 1B, 37 containers start successfully, then:
```
```

## tmpfs

## Enable memory overcommit
`echo 1 > /proc/sysm/vm/overcommit/memory`
=> 70 containers

## tmpfs
Idea: create a tmpfs (RAM filesystem) for /var/lib/docker so creating container don't depend on SD card performances


## run without docker 
mostly to get some metrics on the system limits to run a large number of http servers. Disable unused kernel modules



## Use Go 1.5 for Docker
Go 1.5 has a better GC which could help reduce Docker daemon memory consumption


