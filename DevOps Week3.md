# DevOps Week3 (7/25)
## 멀티 스테이지 빌드
* 도커 이미지 빌드전에 어플리케이션 빌드해야 한다
* 이미지는 되도록이면 작게 해야한다. 특히 개발 패키지 같은 필요없는 건 최대한 넣지 말 것
* 그러나, 어플리케이션 빌드 부분 + 도커 이미지 빌드 부분을 하나의 Dockerfile 에 포함하고 싶은 경우도 있음. 이런 경우에 `멀티 스테이지 빌드`를 활용!
* buildkit 빌드
	* 빌드를 반복하면서 docker-content 사이즈가 커져서 빌드 시간이 오래걸리는 이슈
	* DOCKER_BUILDKIT 환경변수 추가
	* `DOCKER_BUILDKIT=1`
	* 

## nGrinder
* 서버에 대한 성능 테스트를 위한 오픈소스. 트래픽을 만들어서 쏘는 구조
*  성능테스트를 위한 웹UI. 
*  Agent와 Controller


## ETC
docker run 할때 포트를 범위로 지정해서 바인딩 시킬수도 있다. -p 12001-12009:12001-12009

## Volume 
* 호스트와 볼륨 바인딩을 하지 않으면 저장위치는 호스트 서버내 도커가 관리하는 영역
	* /var/lib/docker/volume



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg2NTUzMjI4NCwxMDkxMjQ0MTIwLDc4NT
MwNDY5NiwtOTY5ODk4NDA2LDYwNDY4NTk1MiwtMTExOTk0MDkx
NSwxMDE0MTMyNjQ3LDU2MjYxODE0N119
-->