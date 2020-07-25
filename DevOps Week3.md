# DevOps Week3 (7/25)
## 멀티 스테이지 빌드
* 도커 이미지 빌드전에 어플리케이션 빌드해야 한다
* 이미지는 되도록이면 작게 해야한다. 특히 개발 패키지 같은 필요없는 건 최대한 넣지 말 것
* 그러나, 어플리케이션 빌드 부분 + 도커 이미지 빌드 부분을 하나의 Dockerfile 에 포함하고 싶은 경우도 있음. 이런 경우에 `멀티 스테이지 빌드`를 활용!
* buildkit 빌드
	* 빌드를 반복하면서 docker-content 사이즈가 커져서 빌드 시간이 오래걸리는 이슈
	* DOCKER_BUILDKIT 환경변수 추가
	* 




<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc0MTE2NjYxMSw2MDQ2ODU5NTIsLTExMT
k5NDA5MTUsMTAxNDEzMjY0Nyw1NjI2MTgxNDddfQ==
-->