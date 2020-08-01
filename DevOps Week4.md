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
* 

## Tools
* Build Kit: Fast Image Build
* gocd : CI/CD Server Opensource
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzM2NTMzNzYwLDE3OTUxOTg2ODUsLTg2OD
EyNDU2LC05MDU5NTgzNDMsMTcyNjQ2MDAzNiwyMDkzNDE0NzE2
LC05ODQ1ODQwNjYsMjEwMjY2NzU4MywtMTk1NDEzMzUyMCwxOT
I1MzI2ODYwLC0xNTU0Njc0NzAsLTc1MTQ2NzMwMV19
-->