# 1. 베이스 이미지 설정 (Nginx)
FROM nginx:latest

# 2. 호스트의 index.html을 컨테이너 내부의 Nginx 기본 경로로 복사
COPY index.html /usr/share/nginx/html/index.html

# 3. 80번 포트 개방 (정보 제공용)
EXPOSE 80
