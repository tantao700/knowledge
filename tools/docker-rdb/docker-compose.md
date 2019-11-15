

# Docker-Compose


### 1. Feature 
- 도커 컴포즈는 multi-container Docker applications을 돌리기 위한 Tool
- 매번 run 명령어에 옵션을 설정해 CLI로 컨테이너를 생성하는 방법을 탈피
- 서비스 단위, 프로젝트>서비스>컨테이너
- docker-compose.yml 파일은 서비스들의 집합체
- 하나의 서비스로 여러개의 컨테이너를 정의할 수도 있음
- 컨테이너 순차적 생성 및 구동
- 소규모의 컨테이너 개발환경에서는 도커 엔진의 run 명령어가 더 적합할 수 있음
- 어떠한 설정도 하지 않으면, 현재 디렉토리의 docker-compose.yml 파일을 읽어 도커엔진에게 요청
- 들여쓰기는 짝수 단위  2<4<6 ..


### 2. Use Case
- Development environments
- Automated testing environments
- Single host deployments
 
### 3. Version
| Compose file format | Docker Engine release |
|---------------------|-----------------------|
| 3.7                 | 18.06.0+              |
| 3.6                 | 18.02.0+              |
| 3.5                 | 17.12.0+              |
| 3.4                 | 17.09.0+              |
| 3.3                 | 17.06.0+              |
| 3.2                 | 17.04.0+              |
| 3.1                 | 1.13.1+               |
| 3.0                 | 1.13.0+               |
| 2.4                 | 17.12.0+              |
| 2.3                 | 17.06.0+              |
| 2.2                 | 1.13.0+               |
| 2.1                 | 1.12.0+               |
| 2.0                 | 1.10.0+               |
| 1.0                 | 1.9.1.+               |

### 4. docker-compose.yml

```dockerfile
version: '3'
services:
  db:
    image: microsoft/mssql-server-linux:latest
    ...
    
  app:
    image: cmchoi/java-server:latest
     ...
```


### 5. container naming

- docker compose는 컨테이너를 프로젝트 및 서비스 단위로 구분
- 컨테이너 이름은 [project_name] _ [service_name] _ [container_number]
- compose.yml 파일에서 컨테이너 이름 지정 가능



# Command

![command](https://linuxhint.com/wp-content/uploads/2017/10/command.png)

### 1) build

- 이미지 생성

```bash
$ docker-compose build [options] [--build-arg key=val...] [SERVICE...]
```

### 2) up

- 컨테이너 생성 및 구동
- -f 옵션으로 .yml 파일 지정 가능

```bash
$ docker-compose up -d -f docker-compose-dev.yml
```

### 3) down

- 컨테이너 중지 및 삭제

```bash
$ docker-compose down
```


### 4) start

- 생성된 서비스 실행
```bash
$ docker-compose start mysql
```


### 5) stop

- 실행중인 서비스 중지
```bash
$ docker-compose stop mysql
```


### 6) exec

- 실행중인 컨테이너의 command excute
```bash
$ docker-compose exec -it mysql /bin/bash
```

### 7) scale

- 서비스에 대한 컨테이너 수 설정
```bash
$ docker-compose scale mysql=2
```
