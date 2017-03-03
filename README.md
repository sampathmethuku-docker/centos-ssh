###Introduction:



###build with proxy:
```
docker build  --build-arg http_proxy=http://www-proxy.us.oracle.com:80 --build-arg https_proxy=http://www-proxy.us.oracle.com:80 -t sampathmethuku/centos-ssh:latest .
```
###build with out proxy: 

docker build  -t sampathmethuku/centos-ssh .



###upload image:
docker login
docker push sampathmethuku/centos-ssh:latest




###create the container using --privileged as following:

docker run --privileged  -P -td -e "container=docker"  -v /sys/fs/cgroup:/sys/fs/cgroup  sampathmethuku/centos-ssh  /usr/sbin/init


###how-toConnect:
docker exec <<container-id>> hostname -I 
ssh <<ip>>


### see maping port for 22

docker port <<container-id>>

try access from remote:
ssh -p <<maping-port>> root@<docker-host>

ex : ssh -p 32769 root@slc12nct.us.oracle.com



##Reference:
https://github.com/systemd/systemd/issues/589
https://kuldeeparya.wordpress.com/2015/05/08/dockerfile-dockerizing-sshd-daemon-on-centos

https://docs.docker.com/engine/examples/running_ssh_service
http://stackoverflow.com/questions/28134239/how-to-ssh-into-docker