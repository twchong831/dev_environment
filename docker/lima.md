# Lima

## set lima for docker

[참조](https://qiita.com/akinami/items/d38b9e7c7f37bd070f40)

### Install

```powershell
brew install wget
brew install lima # for docker daemon
brew install docker # for docker
brew install docker-compose
```

#### Init

- docker 세팅을 위한 파일 다운로드

```powershell
wget https://github.com/lima-vm/lima/raw/master/examples/docker.yaml
```

- docker.yaml 파일을 수정

```yml
# 각 항목을 추가
# mounts:
# location: "~"
writable: true

# docker hw 할당
cpus: 2
memory: "8GiB"
disk: "20GiB"

# ssh에 의해 에러가 일어날 가능성이 있다고 함
ssh:
  loadDotSSHPubKeys: false
  localPort: 60006
```

- 파일 수정이 완료되면 가상환경 생성

```powershell
limactl start ./docker.yaml
```

- 가상 환경을 변경하고자 할 경우에는 기존 환경을 삭제하고
- 재생성하여야 함

```powershell
# stop
limactl stop docker
# remove
limactl rm docker # docker : name
```

#### 환경 변수 설정

- .zshrc 파일 수정

```powershell
export DOCKER_HOST=unix:///${HOME}/.lima/docker/sock/docker.sock
```

- 컴퓨터 시작 시 가상환경이 자동으로 시작되고 싶다면 다음을 .zshrc에 추가

```powershell
limactl start docker
```

- 위를 통해 docker를 구동하기 위한 가상 환경 구축은 완료

## docker 환경 구축

```powershell
docker
```

- lima 세팅 전에는 docker 명령어 시 오류가 발생하지만,
- lima 세팅 후에는 정상 동작하는 것을 확인할 수 있음

### image download

```powershell
docker search ubuntu  # ubuntu : 이미지 이름
docker pull ubuntu:18.04 # ubuntu 18.04 버전을 다운로드
docker images     # 다운 받은 이미지를 확인할 수 있음
```

### container 생성

```powershell
docker create -i -t --name [name] ubuntu:18.04
# -i와 -t는 컨테이너와 상호 입출력을 가능하게 하는 옵션
# --name : 컨테이너 이름을 지정
```

### container 작동

```powershell
docker start [name]  # container 실행
docker attach [name] # container 접속
```

## VSCODE를 통한 원격접속

- vscode에서 지원하는 플러그인을 설치
- remote-containers와 Docker 플러그인 설치

### settings.json 수정

- [F1] 키를 통해 settings.json 파일을 로드
- 다음 항목 추가

```powershell
# add
"docker.host": "unix:///Users/twchong/.lima/docker/sock/docker.sock"
```

- vscode의 docker 창에서 container를 확인할 수 있음

## 추가 확인 필요

### network

- container 상에서는 ifconfig를 통해 171.17. 단 IP를 확인할 수 있는데
- macos 상에서는 해당 IP를 확인할 수 없어서 상호 통신이 가능한지 추가 확인 필요함
