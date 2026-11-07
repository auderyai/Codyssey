# 1. 베이스 이미지 설정 (Nginx 최신 버전)
FROM nginx:latest

# 2. 작성한 index.html 파일을 컨테이너의 웹 서버 경로로 복사
COPY index.html /usr/share/nginx/html/index.html

# 3. 외부 노출 포트 설정
EXPOSE 80
