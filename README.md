# Ansible dokcer

##   Ubuntu-sshd-python.  
```
docker run -d -P --name test_sshd    ibackchina2018/ubuntu-sshd:1804  


docker run -d -P --name test_sshd    ibackchina2018/ubuntu-sshd-python3:1804


docker run -d -P --name test_sshd    ibackchina2018/ubuntu-sshd-python38:1804

```

##   Ubuntu 20.04 Desktop Docker with vnc

```
docker run -d  -p 6080:80 -p 5900:5900 -v /dev/shm:/dev/shm dorowu/ubuntu-desktop-lxde-vnc

```


一次开10个：

```
for i in `seq 0 9`;do docker run -itd -p 608$i:80 -v /dev/shm:/dev/shm  dorowu/ubuntu-desktop-lxde-vnc;done


```

参考：    https://hub.docker.com/r/dorowu/ubuntu-desktop-lxde-vnc/      




#  Doc for ansible 
https://docs.ansible.com/



-----------------



# Lab0  Ubuntu with sshd 

**Original docker image**

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


#  **UPDATE 1**

## new docker image with Python2 inside

https://hub.docker.com/repository/docker/ibackchina2018/ubuntu-sshd

```
docker pull ibackchina2018/ubuntu-sshd:1804
```




#  **UPDATE 2**

## new docker image with Python3 inside

https://hub.docker.com/repository/docker/ibackchina2018/ubuntu-sshd-python3

```
docker pull ibackchina2018/ubuntu-sshd-python3:1804
```




-------


**START**

```

git clone  https://github.com/latermonk/Ansible.git

```


# Lab1 启动10个docker并控制

任意起10个dokcer ,使用root/root登录控制

```
for i in `seq 0 9`;do docker run -itd -p 809$i:22 ibackchina2018/ubuntu-sshd:1804;done

```

**需要下次启动docker的时候自启动的话，加 --restart always **
```
for i in `seq 0 9`;do docker run --restart always -itd -p 809$i:22 ibackchina2018/ubuntu-sshd:1804;done

```


##   测试虚拟主机的可用性
```
ansible -k all -m ping
```




**Docker mirror:**
https://hub.docker.com/repository/docker/ibackchina2018/ubuntu-sshd

**Add python on the rastasheep/ubuntu-sshd docker mirror**
[https://hub.docker.com/r/rastasheep/ubuntu-sshd ]



**ansible test**

```
ansible all -m shell -a "apt update && apt install nload -y" 

```


#  Lab2 install nginx on ubuntu1804 with command line

```
for i in `seq 0 9`;do docker run -itd -p 809$i:22 -p 5000$i:80  ibackchina2018/ubuntu-sshd:1804;done
```

```
ansible all -m shell -a "apt update && apt install nginx  -y && nginx "

```

**或者**


```
ansible all  -m apt -a "name=nginx update_cache=yes" 


ansible all -m service -a "name=nginx state=restarted"

```


#  Lab3 install nginx on ubuntu1804 with playbook

```
for i in `seq 0 9`;do docker run -itd -p 809$i:22 -p 5000$i:80  ibackchina2018/ubuntu-sshd:1804;done
```


```
ansible-playbook play.yaml

```



**playbook.yaml**

```
- hosts: all
  user: root
  
  tasks:
  - name:  update apt
    apt:
      name: apt
      state: latest
  - name:  install nginx 
    apt: 
      name : nginx 
      state : latest
  - name:  start nginx
    service:
      name: nginx
      state: started


```

# Lab4 A simple website demo

**code in the Lab4 dirtecory ** 

** first boot 10 docker machine ** 

```

for i in `seq 0 9`;do docker run -itd -p 809$i:22 -p 5000$i:80  -p 4000$i:443  ibackchina2018/ubuntu-sshd-python3:1804;done

```


```

ansible-playbook  web-notls.yml/web-notls.yml

ansible-playbook  web-notls.yml/web-tls.yml

```


 
 


------------------

# ansiblebook
https://github.com/ansiblebook/ansiblebook/tree/1st-edition


https://github.com/ansiblebook/ansiblebook/tree/2nd-edition


# ansible UI   rundeck 
https://docs.rundeck.com/docs/manual/


