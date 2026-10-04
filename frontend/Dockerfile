FROM nginxinc/nginx-unprivileged:alpine
COPY frontend/nginx.conf /etc/nginx/conf.d/default.conf
COPY frontend/index.html /usr/share/nginx/html/index.html
COPY frontend/week5.html /usr/share/nginx/html/week5.html
COPY frontend/week6.html /usr/share/nginx/html/week6.html
EXPOSE 8080