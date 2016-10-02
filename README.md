#centos-php
> 외국의 사이트들이 데비안 계열 리눅스 호스팅을 많이 사용하는데 반해 국내는 redhat 계열, 특히 centos 를 많이 사용하는 것 같습니다.
그래서 docker를 이용해서 centos 기반으로 php 개발환경을 만들어봤습니다.

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

`

docker-compose up -d

`
