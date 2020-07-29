# GKE

## Cluster 접속
gcloud console
`gcloud container clusters get-credentials cluster-1 --region asia-northeast3 --project lge-pri-anthos-poc`

- Cluster 정보 확인: `kubectl cluster-info`
- node 수 확인: `kubectl get nodes`




## Q&A
- 클러스터 기동후에는 잠시 정지 같은 기능은 없나? Stop
- 지금 gcloud 콘솔로 들어와서 만지고 있는 곳은 Master Node?
- npm install 이런게 실제로 구동되고 있는 것도 Master Node?
- 



> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMDUxNDk0NDUsLTc5NTQzNTY5MSwtOT
QzMTU1NjA2XX0=
-->