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

There will be some case case you need additional libraries after making docker. For example, if you need to use the MNE library, run Docker locally, install the libs with pip or apt-get, and then commit & push docker, and the updated version will appear in the docker list.

```
docker run -ti (image name) bash

# Install additional package with 'pip' or 'apt-get' command
# Install all the packages and go back with the 'exit' command

# Making a container with the image
docker commit (container name) (image name)
docker push (image name)
```

### When running the code

Write yaml file and place the code that you want to run in /data/(user name) .

locate yaml file : /home/(user name)
locate data and code : /data/(user name)

In the yaml args part, `cd /home/jinwook && python3 test.py > log.txt` this part executes the code. `cd /home/jinwook` means path access, `python3 test.py > log.txt` means code execution and log generated as txt file.


Command for Initializing the Code in Kube:

Create Job
```
kubectl create -f (file name).yaml
```

End Job
```
kubectl delete pod/(file name)
```

View Job status
```
kubectl get pod

NAME    READY   STATUS      RESTARTS   AGE
torch   0/1     Completed   0          6s
```

View Job Log 
```
kubectl logs (pod name)
```



### Reference & Useful Links

Windows SSH: https://mobaxterm.mobatek.net/

MATLAB Docker Image: https://github.com/mathworks-ref-arch/matlab-dockerfile

Basic Kubectl command: https://subicura.com/k8s/guide/kubectl.html#%E1%84%85%E1%85%B5%E1%84%89%E1%85%A9%E1%84%89%E1%85%B3-%E1%84%8C%E1%85%A6%E1%84%80%E1%85%A5-delete
