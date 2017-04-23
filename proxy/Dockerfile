FROM ssl_nginx

RUN apt-get update && apt-get install -y curl links ; rm -v /etc/nginx/sites-enabled/*
ADD sites-enabled/ /etc/nginx/sites-enabled
