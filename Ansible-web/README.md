#  Ansible-WEB-UI


https://github.com/ansible-semaphore/semaphore   



##   semaphore   


**Ubuntu 18.04**


###  安装mysql
```
docker run -d --name=mysql -p 127.0.0.1:3306:3306 -e MYSQL_ROOT_PASSWORD=my-secret-pw mysql:5.6

```

###  安装ansible

```
apt install ansible  -y
```

###  安装git

```
apt install git  -y 
```

###  下载安装 

https://github.com/ansible-semaphore/semaphore/releases

###  启动生成配置文件
```
semaphore -setup
```
###  再次启动

```
semaphore -config /root/abc/config.json
```
**后台启动**

```
nohup ./semaphore -config /root/abc/config.json &
```
#   访问 3000端口即可


---


![01_Playbook-repo](_image/01_Playbook-repo.png)
![02_key-store](_image/02_key-store.png)
![03_env-store](_image/03_env-store.png)
![04_Inventory](_image/04_Inventory.png)
![05-task-template01](_image/05-task-template01.png)
![05-task-template02](_image/05-task-template02.png)
![06_work-log](_image/06_work-log.png)


