# 🐳 Docker 실습 기록

## 1. Docker 설치 및 기본 점검
Docker 엔진의 설치 상태와 데몬의 정상 동작 여부를 확인합니다.

### 버전 및 정보 확인
- **Docker Version**: `docker --version` 명령을 통해 설치된 버전 확인
- **Docker Info**: `docker info`를 통해 컨테이너, 이미지 개수 및 커널 버전 등 시스템 정보 확인

## 2. Docker 기본 운영 명령 수행
이미지와 컨테이너를 관리하는 기본 명령어를 실습합니다.

### 실습 결과
- **이미지 관리**: `docker pull`, `docker images`를 통한 이미지 확보 및 목록 확인
- **컨테이너 관리**: `docker ps -a`를 통해 실행 중 및 정지된 컨테이너 상태 확인
- **리소스 확인**: `docker stats`를 통해 CPU/Memory 사용량 점검

### 실행 화면
![기본 점검 및 운영](./img/docker-01-basic.png)

---

## 3. 컨테이너 실행 실습
다양한 이미지를 컨테이너로 실행하고 내부 환경을 탐색합니다.

### 실습 내용
- **hello-world**: Docker Hub에서 이미지를 가져와 컨테이너가 정상 실행됨을 확인
- **ubuntu 컨테이너 진입**: `-it` 옵션을 사용하여 컨테이너 내부 쉘(bash)에 접속
- **내부 명령 수행**: 컨테이너 안에서 `ls`, `echo` 등 리눅스 기본 명령어 실행

### 실행 화면
![컨테이너 실행 실습](./img/docker-02-execution.png)

### 💡 관찰 기록: 종료(Termination) vs 유지(Maintenance)
- **종료**: `docker run -it`으로 진입한 후 `exit`를 입력하면, 컨테이너의 메인 프로세스(bash)가 종료되면서 컨테이너도 함께 **Exited (0)** 상태가 됨.
- **유지**: 컨테이너를 죽이지 않고 빠져나오려면 `Ctrl + P + Q`를 사용하거나, `docker exec`를 통해 실행 중인 컨테이너에 접속해야 함.
