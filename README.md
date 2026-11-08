# 🚀 Codyssey 인프라 문서화 프로젝트

이 프로젝트는 리눅스 서버 구축부터 도커 컨테이너 운영, 그리고 Git을 통한 버전 관리까지의 학습 과정을 기록한 문서입니다.

---

## 📂 카테고리 바로가기

1. [Linux 환경 구축 및 권한 관리](./linux/README.md)
2. [Docker 컨테이너 운영](./docker/README.md)
3. [Git & GitHub 연동](./git/README.md)

---

## 🌟 보너스 실습: Docker Compose 멀티 컨테이너 운영

단일 컨테이너 관리를 넘어, 여러 개의 서비스를 하나의 설정 파일로 관리하고 환경 변수를 통해 유연하게 운영하는 실습을 진행했습니다.

### 1. docker-compose.yml 설정 (IaC)
서비스 간의 네트워크 연결과 포트 매핑, 환경 변수 활용을 정의한 소스 코드입니다.

```yaml
# ~/infra-docs/docker/docker-compose.yml
version: '3.8'
services:
  web:
    image: nginx:latest
    ports:
      - "${WEB_PORT:-8080}:80" # .env의 WEB_PORT 사용, 없으면 8080
    networks:
      - infra-net

  cache:
    image: redis:alpine     # 보조 서비스(Redis) 추가
    networks:
      - infra-net

networks:
  infra-net:                # 서비스 간 통신을 위한 전용 네트워크
    driver: bridge
2. 환경 변수 주입 및 실행 결과
.env 파일을 통해 외부에서 설정을 주입하고, 브라우저를 통해 서비스가 정상 동작함을 확인했습니다.

설정값: WEB_PORT=9000 주입
확인 URL: http://localhost:9000
브라우저 접속 확인

3. Compose 운영 워크플로우 실습
터미널 명령어를 통해 컨테이너의 생명주기를 관리한 기록입니다.

실습 순서:

up -d: 백그라운드에서 멀티 컨테이너 실행 및 네트워크 자동 생성
ps: 생성된 web, cache 서비스의 상태 및 포트 매핑 확인
logs -f: Nginx 서버의 접속 로그 실시간 모니터링 (GET 요청 확인)
down: 컨테이너 및 네트워크 일괄 삭제 (자원 정리)
Compose 운영 기록

💡 배움 포인트
IaC: docker-compose.yml을 통해 인프라 설정을 문서화하면 팀원 누구나 동일한 환경을 즉시 구축할 수 있습니다.
유연성: 환경 변수(.env)를 활용하여 소스 코드 수정 없이 포트나 모드를 변경하는 유연성을 확보했습니다.
B. GitHub SSH 보안 설정
SSH Key 생성: 보안 강화된 인증 방식 도입
공개키 등록: GitHub 계정에 SSH 키 등록 및 통신 테스트

### 🔐 Git SSH 인증 및 자동 로그인 설정
단순한 ID/PW 방식에서 벗어나, SSH 비대칭키를 이용한 보안 인증을 설정했습니다.

- **주요 내용**: `ed25519` 알고리즘 기반 키 생성, GitHub 공개키 등록, 원격 저장소 SSH 주소 전환
- **학습 효과**: 보안성 향상 및 `git push` 시 인증 절차 간소화
- **상세 보기**: [Git SSH 설정 가이드](./git/README.md#🔐-git-ssh-인증-설정)

---

## 🛠 기술 스택 및 환경 (Tech Stack & Environment)

이 프로젝트는 아래의 실제 운영 환경에서 구축 및 검증되었습니다.

### 💻 Infrastructure
- **OS**: Ubuntu 24.04.4 LTS (Noble Numbat)
- **VCS**: Git v2.43.0 / GitHub

### 🐳 Container Runtime
- **Docker**: v29.6.2
- **Docker Compose**: v5.3.1

### 🌐 Application Stack
- **Web Server**: Nginx (Latest)
- **Database**: Redis (Latest)
- **Custom Image**: `my-webserver:v2` (Nginx 기반 커스텀 이미지)

---

### 📊 컨테이너 운영 현황 (Container Status)
현재 시스템에서 관리 중인 주요 컨테이너 목록입니다.

| Name | Image | Port | Status |
| :--- | :--- | :--- | :--- |
| **bind-mount-test** | nginx | 8081:80 | Running (Up 4 hours) |
| **my-custom-web** | my-webserver:v2 | 8080:80 | Exited |
| **my-ubuntu** | ubuntu | - | Exited |
| **test-nginx** | nginx | 80 | Exited |