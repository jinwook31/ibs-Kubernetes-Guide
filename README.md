# ibs-Kubernetes-Guide

### SSH 연결

Mac (Terminal): https://eunguru.tistory.com/122

Windows (Putty): https://www.putty.org/ 

File Upload: https://winscp.net/eng/download.php


### 계정 생성 (e8 only): 
```
cd ~/k8s/user-manager 
./user-create.sh (user name) (용량)
```

### [Image 생성 관련]

Docker image pull 하거나 업로드 (필요에 맞게 docker 만들기: https://www.nurinamu.com/dev/2016/07/04/create-a-docker-image/)
```
docker tag (기존이름) well.local:5000/(바꿀 이름)
docker psuh well.local:5000/(이름)
```

### [Image에 추가 Lib 설치 시]

Local에서 Docker 실행 후 설치
```
docker commit (container 이름) (image 이름)
docker push (image 이름)
```

### [코드 실행 시]

yaml 파일 작성 후 실행하려는 코드를 /data/(user name) 위치에 놓기
실행 관련 명령어:
```
kubectl create -f (파일이름).yaml
kubectl delete pod/(파일이름)
kubectl get pod
kubectl logs (pod 이름)
```



### Reference & Useful Links

윈도우 사용시 SSH: https://mobaxterm.mobatek.net/

MATLAB Docker Image: https://github.com/mathworks-ref-arch/matlab-dockerfile

Kubectl 기본 명령어: https://subicura.com/k8s/guide/kubectl.html#%E1%84%85%E1%85%B5%E1%84%89%E1%85%A9%E1%84%89%E1%85%B3-%E1%84%8C%E1%85%A6%E1%84%80%E1%85%A5-delete
