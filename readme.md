# Spring petclinic data jdbc 과제


## * 어플리케이션 빌드 및 배포, 실행방법

과제에 대한 실행은 다음과 같이 3가지의 순서로 진행합니다.

1. Gradle로 어플리케이션 빌드
2. Docker 이미지 빌드 및 Dockerhub에 Push
3. Kubernetes 상에서 배포 및 실행


## 1. Gradle로 어플리케이션 빌드

* gradle clean으로 기존에 빌드된 파일 제거

```shell
$ ./gradlew clean
```

* gradle build로 새로 빌드

```shell
$ ./gradlew bootJar
```


## 2. Docker 이미지 빌드 및 Dockerhub에 Push

* docker build

```shell
$ ./gradlew jib
```

* Push된 이미지명 : skwjdgh1/petclinic:latest


## 3. Kubernetes 상에서 배포 및 실행

* kubernetes/db 디렉토리 내의 Manifest 실행을 통해 Mysql DB Pod, Service 및 데이터 저장용 PV, PVC 배포

```shell
$ kubectl apply -f kubernetes/db/
```

* kubernetes/webwas 디렉토리 내의 Manifest 실행을 통해 Petclinic 어플리케이션용 Webwas Pod, Service 및 Public망에서 어플리케이션 접속용 Ingress 배포

```shell
$ kubectl apply -f kubernetes/webwas/
```
