#centos-php
> docker를 이용해서 centos 기반으로 php 개발환경을 만들어봤습니다. (docker image 중에서 centos를 기반으로 한 php 개발환경을 찾기가 쉽지 않더군요. 우분투가 대세인듯..)
[laradock](https://github.com/LaraDock/laradock) 구조를 참고로 해서 수정하는 형태로 만들었습니다.

##Requirements
- [docker](https://www.docker.com/) 및 [docker-compose](https://docs.docker.com/compose/)

##Base image
centos:6.8

##Containers
1. apache2 - 아파치2 및 php5.6
2. mysql
3. volumes/application -데이터 볼륨 
4. workspace - 작업디렉토리. 이곳으로 들어가서 작업하면 됩니다.

##사용방법
프로젝트 디렉토리에서 

```
docker-compose up -d
```

이미지가 로드완료된 후에 workspace 접속
```
docker exec -it centosphp_workspace_1 bash
```

docker-compose.yml 에서 my-php-app 대신에 자신의 프로젝트 디렉토리로 변경하면 됩니다.

아래의 mysql 컨테이너 변수들도 값을 변경해서 사용할 수 있습니다. 

1. MYSQL_ROOT_PASSWORD
2. MYSQL_DATABASE
3. MYSQL_USER
4. MYSQL_PASSWORD
