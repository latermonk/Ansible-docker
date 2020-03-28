# Ansible dokcer

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




# Lab1 启动10个docker并控制

任意起10个dokcer ,使用root/root登录控制

```
for i in `seq 0 9`;do docker run -itd -p 809$i:22 ibackchina2018/ubuntu-sshd:1804;done

```

**需要下次启动docker的时候自启动的话，加 --restart always **
```
for i in `seq 0 9`;do docker run --restart always -itd -p 809$i:22 ibackchina2018/ubuntu-sshd:1804;done

```



**Docker mirror:**
https://hub.docker.com/repository/docker/ibackchina2018/ubuntu-sshd

**Add python on the rastasheep/ubuntu-sshd docker mirror**
https://hub.docker.com/r/rastasheep/ubuntu-sshd 



**ansible test**

```
ansible all -m shell -a "apt update && apt install nload -y" 

```



