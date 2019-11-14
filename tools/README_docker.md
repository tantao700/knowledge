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

## A:Make the pom setting for java

```xml
<plugin>
    <groupId>com.spotify</groupId>
    <artifactId>docker-maven-plugin</artifactId>
    <version>1.2.1</version>
    <configuration>
        <imageName>${docker.image.prefix}/${project.artifactId}:${project.version}</imageName>
        <dockerDirectory>${project.basedir}/src/docker</dockerDirectory>
        <resources>
            <resource>
                <targetPath>/</targetPath>
                <directory>${project.build.directory}</directory>
                <include>${project.build.finalName}.jar</include>
            </resource>
        </resources>
    </configuration>
</plugin>
```

```Dockerfile
FROM java:8
VOLUME /tmp
ADD *.jar /app.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
```

## A:How to check docker status
```shell
    [ec2-user@ip-10-0-46-113 ~]$ sudo systemctl status docker
    docker.service - Docker Application Container Engine
       Loaded: loaded (/usr/lib/systemd/system/docker.service; enabled; vendor preset: disabled)
       Active: active (running) since Tue 2016-02-02 18:13:42 EST; 2 days ago
         Docs: https://docs.docker.com
     Main PID: 16915 (docker)
       Memory: 14.7M
       CGroup: /system.slice/docker.service
               ├─16915 /usr/bin/docker daemon -H fd://
               └─20162 docker-proxy -proto tcp -host-ip 0.0.0.0 -host-port 3375 -container-ip 172.17.0.2 -container-port 2375               
```

reference：https://success.docker.com/article/using-systemd-to-control-the-docker-daemon
