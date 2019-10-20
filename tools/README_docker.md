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

