# QRding-html：单文件静态版，Nginx 直接托管
FROM nginx:alpine

# 静态文件
COPY index.html /usr/share/nginx/html/index.html

# 精简 Nginx 配置：关闭目录列表、开启 gzip、静态缓存
RUN printf '%s\n' \
    'server {' \
    '    listen       80;' \
    '    server_name  _;' \
    '    root         /usr/share/nginx/html;' \
    '    index        index.html;' \
    '    autoindex    off;' \
    '    gzip         on;' \
    '    gzip_types   text/html text/css application/javascript;' \
    '    location / {' \
    '        try_files $uri $uri/ /index.html;' \
    '    }' \
    '}' > /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
