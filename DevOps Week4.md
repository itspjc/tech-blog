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


## Container Monitorg
- 로그를 이벤트 스트림으로 취급하라
	- 로그파일로 관리하지 말고 stdout 으로 출력
	- 로그파일은 앱이 아닌 실행환경으로 관리한다

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjEwMjY2NzU4MywtMTk1NDEzMzUyMCwxOT
I1MzI2ODYwLC0xNTU0Njc0NzAsLTc1MTQ2NzMwMV19
-->