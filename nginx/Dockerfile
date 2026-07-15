# nginx/Dockerfile
FROM nginx:alpine

# 安装 openssl 用于生成 SSL 证书
RUN apk add --no-cache openssl

# 创建证书存放目录
RUN mkdir -p /etc/nginx/ssl

# 在构建镜像时自动生成自签名 SSL 证书（42 评估免去手动配置）
RUN openssl req -x509 -nodes -days 365 \
    -newkey rsa:2048 \
    -keyout /etc/nginx/ssl/transcendence.key \
    -out /etc/nginx/ssl/transcendence.crt \
    -subj "/C=PT/L=Lisbon/O=42Lisbon/OU=ft_transcendence/CN=localhost"

# 复制 nginx 配置文件
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80 443