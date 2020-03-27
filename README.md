# vagrant-docker-ansible

## Ubuntu with sshd 

```
docker run -d -P --name test_sshd rastasheep/ubuntu-sshd:18.04

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




# Lab

```
起动或者暂停10个dokcer,然后用ansible控制这些docker
```

## 简化
任意起10个dokcer ,使用root/root登录控制
