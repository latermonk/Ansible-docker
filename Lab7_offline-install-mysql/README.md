#   offline-install_mysql



```
ansible-playbook   ubuntu1804-install-mysql.yaml


```



##  Download software needed
```
apt-get install --print-uris mysql-server
```

**put to dir **
```
/var/cache/apt/archives
```


**install mysql**
```
apt-get install mysql-server
```




```
export DEBIAN_FRONTEND=noninteractive && export DEBIAN_PRIORITY=critical && sudo /usr/bin/dpkg -i ./files/*



```


