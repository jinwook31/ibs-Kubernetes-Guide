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



## Docker 

### Docker Image Pull & Upload

- Docker Hub에서 가져오기: https://hub.docker.com/
- 필요에 맞게 Docker 만들기: https://www.nurinamu.com/dev/2016/07/04/create-a-docker-image/). 

프로젝트에 맞는 Docker Image를 가져온 뒤에 추가로 필요한 library는 docker 명령어로 Image에서 설치를 해주면 됩니다. 그리고 이때 주의해야할 점은 꼭 이름 앞에 well.local:5000을 붙여야합니다.

```
docker ps -a
docker images
docker tag (기존이름) well.local:5000/(바꿀 이름)
docker psuh well.local:5000/(이름)
```


### Image에 추가 Lib 설치 시

Docker를 설치했지만 추가적인 라이브러리가 필요한 경우가 있습니다. 예를 들어 MNE 라이브러리를 사용해야하는 경우 Local에서 Docker를 실행 한 후 pip 또는 apt-get 등으로 설치를 한 후에 docker를 commit & push 하면 업데이트된 버젼이 docker 목록에 나타날 것입니다.
```
docker run -ti (image 이름) bash

# pip 또는 apt-get 으로 원하는 package 설치
# 설치 후 exit 으로 나간 뒤 

# 작업한 container를 image로 만들기
docker commit (container 이름) (image 이름)
docker push (image 이름)
```

### 코드 실행 시

yaml 파일 작성 후 실행하려는 코드를 /data/(user name) 위치에 놓습니다.

yaml 파일 위치 : /home/(user name)
data 및 코드 위치 : /data/(user name)

yaml args 부분에 실행 명령어 부분에 `cd /home/jinwook && python3 test.py > log.txt` 이 부분이 코드를 실행하는 부분입니다. `cd /home/jinwook`은 경로 접근, `python3 test.py > log.txt`은 코드 실행 및 생기는 log를 txt 파일로 저장한다라는 의미입니다.


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

NAME    READY   STATUS      RESTARTS   AGE
torch   0/1     Completed   0          6s
```

Job Log 조회
```
kubectl logs (pod 이름)
```



### Reference & Useful Links

윈도우 사용시 SSH: https://mobaxterm.mobatek.net/

MATLAB Docker Image: https://github.com/mathworks-ref-arch/matlab-dockerfile

Kubectl 기본 명령어: https://subicura.com/k8s/guide/kubectl.html#%E1%84%85%E1%85%B5%E1%84%89%E1%85%A9%E1%84%89%E1%85%B3-%E1%84%8C%E1%85%A6%E1%84%80%E1%85%A5-delete
