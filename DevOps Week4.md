# DevOps Day4

docker build -t hello-node:v2
kubectl set image deployment/hello-node hello-node=hello-node:v2

## K3S
* 경량화된 Kubernetes
* IoT, 엣지단에서 많이 쓰는듯

## Docker Host Monitoring
- htop
- glances
	- CUI
	- GUI: Web Console 로 띄울 수 있음
	- [http://localhost:61208/10](http://localhost:61208/10)
	- 10초 간격으로 띄우기
	- api 로 특정 정도만 볼 수도 있다


## Container Monitoring
- **로그를 이벤트 스트림으로 취급하라**
	- 로그파일로 관리하지 말고 stdout 으로 출력
	- 로그파일은 앱이 아닌 실행환경으로 관리한다
	- docker logs, docker-compose logs 로 볼 수 있게 표준 출력으로 로그를 출력할 수 있게 어플리케이션을 구성할 것
	- Docker 에 들어가서 보는 것은 비추천
- **frontail**
	- 로그 스트림을 브라우저로 보여주는 노드 어플리케이션

## Multi Host Monitoring
ELK를 이용한 로그분석 환경 구축  
* `Elastic Search` + `Logstash` + `Kibana` + (`Redis`)
* Redis 로 트래픽에 대비하여 중간 버퍼를 두는 것 (캐시 서버로도 씀)
* ES -> kibana -> Redis 순으로 설치 (kibana 가 Elastic Search 를 바라봐야 함)
* Redis는 보통 3배수로 띄움
* 이거 우리 프론트에도 달아보면 되겠는데?
* [https://github.com/deviantony/docker-elk](https://github.com/deviantony/docker-elk)

## Security
* --privileged 명령어는 쓰지마라. 이거 쓰면 docker 명령어 거의 다 쓸 수 있음. (/var/run/docker.sock 볼륨마운트 하는거랑 비슷)
* Docker Security Scanning: 이미지 보안 취약점을 스캔해서 알려줌 (현재는 유료)
* Docker Bench: Open Source scanning service
	* [https://github.com/docker/docker-bench-security](https://github.com/docker/docker-bench-security)

## Micro Service 특징
* 심플하며 개발 요구사항에 특화되어 있다
* 개별 팀에서 독립적인 개발/배포가 가능 -> 그런 환경들이 마련되어야 특징을 잘 살릴 수 있다
* 각각의 서비스는 다른 프로그래밍 언어, 개발 도구로 개발 가능
* 문제점:
	* 서비스 범위를 어떻게 설정? 얼마나 작아야, 어느정도 범위에서 나누어야 하는지
		* 용어의 문제 Cloud Native ? 
		* Domain 분석을 통해 마이크로 서비스의 범위를 정하는 방법 밖에 없다. Domain Driven Design
	* 레거시 시스템: Moby Project (기존 시스템을 마이크로 서비스화 하기 위한 도커사의 프로젝트?)
	* 운영 이슈
		* DevOps
	* 중복 이슈
		* miniservices: multiple services domain sharing same data store
		* to build microservices, data store would be NO-SQL finally.
	* 복잡도
	* 분산 이슈
		* Actor Model : akka.io /JVM 에서 동작, 
* BoundedText

## RESTful API
* 리소스 단위로 표현이 가능해야함
	* GET /companies/3/employees
* HTTP Method
	* GET, POST, PUT, DELETE
* 가능한 따르려고 노력을 하나, 100% 만족하기는 어렵다...
* Response code
	* 2xx: success, 3xx: redirect, 4xx: client error, 5xx: server error
* Versioning 
	* api.com/v1/xxxx

## DevOps
System Administrator: 이제 없어져가고 있는 직업. DevOps 엔지니어로 전향하든가 그만두든가 하고 있다.  
DevOps Engineer 가 각광받을듯. (인프라나 자동화에 관심이 많다면 강력하게 추천함)

코드리뷰: phabricator? 


## Tools
* Build Kit: Fast Image Build
* gocd : CI/CD Server Opensource

k16wire@gmail.com

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM4OTY2OTQ3MiwtMTkwOTUwMzgwOCwxMT
Q1NDc5NzkwLC03MzI1NzQ2MTksNDk1ODA2NjM3LDcwMjcwNzA4
OSwxOTE1Mzg1MjIzLC00ODM1MTA4NzEsMjEzODg4NjI5NywxNz
k1MTk4Njg1LC04NjgxMjQ1NiwtOTA1OTU4MzQzLDE3MjY0NjAw
MzYsMjA5MzQxNDcxNiwtOTg0NTg0MDY2LDIxMDI2Njc1ODMsLT
E5NTQxMzM1MjAsMTkyNTMyNjg2MCwtMTU1NDY3NDcwLC03NTE0
NjczMDFdfQ==
-->