# 🐳 Docker 실습 및 이미지 빌드

이 디렉토리는 Docker의 기초 운영부터 Dockerfile을 이용한 커스텀 웹 서버 이미지 빌드 과정을 기록한 문서입니다.

## 1. 프로젝트 구조
현재 디렉토리에 포함된 주요 파일들입니다.
- `Dockerfile`: Nginx 기반의 커스텀 이미지 빌드 설정 파일
- `index.html`: 웹 서버에서 출력될 메인 페이지 (UTF-8 적용)
- `img/`: 실습 증빙 스크린샷 모음

## 2. 주요 실습 내용
1. **Docker 설치 및 상태 확인**: `docker version`, `docker info`
2. **컨테이너 운영**: `run`, `ps`, `logs`, `stats` 명령어 숙달
3. **커스텀 이미지 빌드**: Dockerfile을 활용한 이미지 생성
4. **포트 매핑**: 호스트 8080포트와 컨테이너 80포트 연결

## 3. 실습 증빙 (Screenshots)
### 3.1 Docker 운영 및 상태 확인
![Docker 운영](./img/docker-02-ops.png)

### 3.2 커스텀 이미지 빌드 과정
![이미지 빌드](./img/docker-04-build.png)

### 3.3 최종 브라우저 실행 화면 (성공)
![브라우저 결과](./img/docker-05-browser-success.png)

---

## 4. 소스 코드 (Source Code)

### [Dockerfile](./Dockerfile)
```dockerfile
# Nginx 베이스 이미지 사용
FROM nginx:latest
# 로컬의 index.html을 컨테이너 내부로 복사
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
index.html
html
📋 복사
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>My Docker Webserver</title>
</head>
<body>
    <h1>Hello, Docker!</h1>
    <p>한글 인코딩이 정상적으로 적용된 화면입니다.</p>
</body>
</html>

