# Ansible dokcer

#  Doc for ansible 
https://docs.ansible.com/



-----------------



# Lab0  Ubuntu with sshd 

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

Lab4 Role

```
 mkdir -pv ansible_playbooks/roles/{websrvs,dbsrvs}/{tasks,files,templates,meta,handlers,vars}
 
 ```
 
 


------------------


# ansible UI   rundeck 
https://docs.rundeck.com/docs/manual/


