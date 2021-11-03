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

![user_create](https://raw.githubusercontent.com/jinwook31/ibs-Kubernetes-Guide/main/img/user%20create.PNG)

초기 설정으로는 id: (user name), pw: (user name)으로 동일합니다. 비밀번호를 수정하기 위해서는 해당 계정으로 로그인 후에 아래 명령어로 수정해주면 됩니다.

```
passwd
```


### [Image 생성 관련]

Docker image pull 하거나 업로드 (필요에 맞게 docker 만들기: https://www.nurinamu.com/dev/2016/07/04/create-a-docker-image/). 

이때 주의해야할 점은 꼭 이름 앞에 well.local:5000을 붙여야합니다.
```
docker tag (기존이름) well.local:5000/(바꿀 이름)
docker psuh well.local:5000/(이름)
```


### [Image에 추가 Lib 설치 시]

Docker를 설치했지만 추가적인 라이브러리가 필요한 경우가 있습니다. 예를 들어 MNE 라이브러리를 사용해야하는 경우 Local에서 Docker를 실행 한 후 pip 또는 apt-get 등으로 설치를 한 후에 docker를 commit & push 하면 업데이트된 버젼이 docker 목록에 나타날 것입니다.
```
docker 실행 명령어 @@@

docker commit (container 이름) (image 이름)
docker push (image 이름)
```

### [코드 실행 시]

yaml 파일 작성 후 실행하려는 코드를 /data/(user name) 위치에 놓기
실행 관련 명령어:

Job 생성
```
kubectl create -f (파일이름).yaml
```

Job 종료
```
kubectl delete pod/(파일이름)
```

Job 상태 조회
```
kubectl get pod
```

Job Log 조회
```
kubectl logs (pod 이름)
```


### Reference & Useful Links

윈도우 사용시 SSH: https://mobaxterm.mobatek.net/

MATLAB Docker Image: https://github.com/mathworks-ref-arch/matlab-dockerfile

Kubectl 기본 명령어: https://subicura.com/k8s/guide/kubectl.html#%E1%84%85%E1%85%B5%E1%84%89%E1%85%A9%E1%84%89%E1%85%B3-%E1%84%8C%E1%85%A6%E1%84%80%E1%85%A5-delete
