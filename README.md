## 0.0 Docker란
- Image
  - 개발환경(컨테이너)을 찍어내는 틀
- 도커 컨테이너는 OS와 상관없이 linux 가상환경 형태로 돌아감
## 0.1 Docker Website
- [Docker Hub](https://hub.docker.com/)

## 1.0 Docker 명령어
```shell
docker run -it node
```
  - `-it`: 컨테이너 생성 후 환경 안 CLI 사용하기
```shell
docker images
```
현재 소유하고 있는 도커 이미지들
```shell
docker ps
docker ps -a # 모든 실행가능한 컨테이너
```
- 현재 작업중인 컨테이너 정보를 테이블형으로 제시한다
```shell
docker exec -it CONTAINER_NAME bash
```

```shell
docker stop $(docker ps -aq)
docker system prune -a
```

Dockerfile
- 나만의 이미지를 만들기 위한 설계도
- 기존 이미지에 프로젝트에중필요한 패키지를 설치한 이미지를 만드는것것
```shell
FROM node:12.18.4 # Base로 사용할 Image
RUN npm install -g http-server # 이미지를 생성하는 과정에서 실행되는 명령어
WORKDIR /home/node/app # 명령어를 실행할 위치
CMD # 컨테이너가 가동되는 중 실행한 명령어를 WORKDIR에 실행함
```

```shell
docker build -t IMAGE_NAME 상대경로
```
- 파일명이 Dockerfile이면 상대경로는 `.`

```shell
docker run --name frontend-con -v $(pwd):/home/node/app -p 8080:8080 frontend-img
```
-v: 내부의 폴더를 외부의 폴더와 연결짓기

COPY 이미지 생성과정에 미리 특정 파일을 넣어둠
