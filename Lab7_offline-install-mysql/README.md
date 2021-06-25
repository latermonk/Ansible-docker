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



#  INSTALL
```

dpkg -i libaio1_0.3.110-5ubuntu0.1_amd64.deb
dpkg -i libssl1.1_1.1.1-1ubuntu2.1~18.04.9_amd64.deb   需要手动
dpkg -i mysql-common_5.8+1.0.4_all.deb
dpkg -i *.deb   


```




