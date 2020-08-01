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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NTQxMzM1MjAsMTkyNTMyNjg2MCwtMT
U1NDY3NDcwLC03NTE0NjczMDFdfQ==
-->