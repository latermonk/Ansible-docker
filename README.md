# vagrant-docker-ansible

## Ubuntu with sshd 

```
docker run -d -P --name test_sshd rastasheep/ubuntu-sshd:14.04

```
**check port of this docker**

```
docker port test_sshd 22
```
**ssh to the docker **
```
 ssh root@localhost -p 49154
```

https://hub.docker.com/r/rastasheep/ubuntu-sshd   



## a
