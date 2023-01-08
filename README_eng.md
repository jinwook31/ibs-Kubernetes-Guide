# ibs-Kubernetes-Guide

### SSH Connection

Mac (Terminal): https://eunguru.tistory.com/122

Windows (Putty): https://www.putty.org/ 

File Upload: https://winscp.net/eng/download.php



### Make new user account (e8 only): 
```
cd ~/k8s/user-manager 
./user-create.sh (user name) (용량)
```

![user_create](https://raw.githubusercontent.com/jinwook31/ibs-Kubernetes-Guide/main/img/user%20create.PNG)

For initial setting -> id: (user name), pw: (user name)  id and pw is equal. In order to change the password, you need to log-in and use the command below.
```
passwd
```



## Docker 

### Docker Image Pull & Upload

- Import from Docker Hub (Good way to start making Docker Image): https://hub.docker.com/
- Create Docker to fit your needs: https://www.nurinamu.com/dev/2016/07/04/create-a-docker-image/).

After importing the Docker Image suitable for the project, additionally required libraries can be installed from the Image with the docker command. The thing to be careful about at this is to put the 'well.local:5000' in front of the name.

```
docker ps -a
docker images
docker tag (prev name) well.local:5000/(new name)
docker psuh well.local:5000/(Docker image name)
```


### Adding new Library to the Image

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
