FROM centos:7

MAINTAINER hardcattle@gmail.com

ENV NGINX_VERSION 1.14.0

RUN CONFIG="\
		--prefix=/usr/local/nginx/ \
		--user=nginx \
		--group=nginx \
	" \
	&& yum update -y \
	&& yum install -y curl gcc pcre pcre-devel zlib zlib-devel openssl openssl-devel libxml2 libxml2-dev libxslt-devel \
	&& groupadd nginx \
	&& useradd -s /sbin/nologin -g nginx nginx \
	&& curl -fSL https://nginx.org/download/nginx-$NGINX_VERSION.tar.gz -o nginx-$NGINX_VERSION.tar.gz \
	&& tar xzf nginx-$NGINX_VERSION.tar.gz \
	&& cd nginx-$NGINX_VERSION \
	&& ./configure $CONFIG \
	&& make -j$(getconf _NPROCESSORS_ONLN) \
	&& make install \
	&& rm -rf nginx-$NGINX_VERSION.tar.gz \
	&& rm -rf nginx-$NGINX_VERSION

EXPOSE 80 443

CMD ["/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]                                                                                                                                                                                   