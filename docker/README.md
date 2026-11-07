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
