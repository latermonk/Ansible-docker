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

```
for i in `seq 0 9`;do docker run -itd -p 809$i:22 ibackchina2018/ubuntu-sshd:1804  ;done

```


###  启动dokcer  ubuntu-sshd

```
for i in `seq 0 9`;do docker run -itd -p 809$i:22 rastasheep/ubuntu-sshd:18.04  ;done

```

**安装 Python**

```
 apt install python-minimal
 
 ```
 
 
 **ibackchina2018/ubuntu-sshd:1804**
 
 
 
 
### ansible控制
