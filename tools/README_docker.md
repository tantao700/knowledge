# how to setup the docker api


## docker tools
    - k8s
    - portainer.io


## A:How to setup the docker remote port    
Q:create the file with below content
```text
# for CentOS
# step 1
[root@localhost docker.service.d]# cat /etc/systemd/system/docker.service.d/tcp.conf
[Service]
ExecStart=
ExecStart=/usr/bin/dockerd -H unix:///var/run/docker.sock -H tcp://0.0.0.0:2375

# step 2 restart the service
service docker restart
```

