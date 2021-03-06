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
	* 예를 들어, 나스 전체를 저기랑 바운딩을 시키면 전체를 그냥 쓸 수 있음
* 컨테이너와 라이프 사이클이 같은 데이터들은 그냥 컨테이너에 저장하는게 나음. 관리가 훨씬 쉽다
* 클라우드 프로바이더 볼륨 마운트
	* 호스트의 데이터 영역도 망가졌을 경우에 유용
	* Storage-Driver 를 이용해 네트워크로 연결된 장치에 저장 
* read-only  등으로도 생성 가능함


## Networking
* docker0 가 bridge
* bridge: 단일 호스트내에서 컨테이너를 연결해주는 네트워크
* overlay: 멀티 호스트간에 연결해주는 네트워크

### overlay network
* 도커엔진은 overlay 네트워크 드라이버를 통해 멀티 호스트 네트워크 지원
 
## Docker Swarm
 * Swarm Cluster: Swarm 을 이용해 구축한 클러스터
	 * Manager Node
	 * Worker Node
 * Token
	 * `docker swarm join-token manager`
	 * `docker swarm join-token worker`
 * Swarm Kit
 * 도커만 가지고 클러스터를 구축할 수 있다는 매력을 가지고 있음. 다만 Kubernetes 보다는 정교하지 못하다.

## Kubernetes
* Made by Google, Use to ochestrate docker containers.
* The best documents is Kubernetes official spec documentation.
* Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications.

### 가장 먼저 해야 할 일
* k8s 클러스터 설치: 컨테이너 애플리케이션을 실행하는 노드 == 워커 노드의 집합.

### POD
* 하나의 Pod는 여러개의 컨테이너를 가진다. (여러 타입의 컨테이너가 들어갈 수 있음)
* Docker Swarm 은 하나의 Task에는 한 타입의 컨테이너만 들어갈 수 있음
* 하나의 Pod은 한 호스트에 들어있는 것. 여러 호스트에 걸쳐있을 수 없다. (Pod 내에 있는 컨테이너끼리는 로컬콜)


### Service
Pods는 늘어나거나 줄어들 수 있어, Pods로 가는 트래픽을 load balancing 해줄 수 있어야 하는데, 그 역할을 Service가 수행함
* Private IP: 외부에 서비스를 할 **필요가 없는 경우**
* Public IP: 외부에 서비스를 노출할 필요가 있는 경우

### kube-controller-manager
* Deployment > ReplicaSet > Pod
* Job, CronJob

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcwMDEzMzQ0OCwxNDM4MTQyMzg2LC0xMD
gxMDUyMjU0LC0yMTAwNDM0OTQzLC0xOTMxNjE1MTQ0LDgzMzUx
NzczMCw5NDgzNzA1ODQsNzY1ODI3NDM4LC0xNTc2MzA0MDA4LD
E2OTc4NjU5NzUsLTQ3NTM3NTI5Miw4MzE4NTYxMjIsLTMxMTM2
NzY4MiwtMTQ2NTgxNjU1MSwtMTEyNDYzMTQ3LDEwOTEyNDQxMj
AsNzg1MzA0Njk2LC05Njk4OTg0MDYsNjA0Njg1OTUyLC0xMTE5
OTQwOTE1XX0=
-->