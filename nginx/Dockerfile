FROM ubuntu:16.04 as build

#
RUN mkdir /nginx

#
WORKDIR /nginx

RUN set -x && \
	apt-get update && \
	apt-get install --no-install-recommends --no-install-suggests -y \
			wget git lbzip2 build-essential libssl-dev  ca-certificates   \

	&& wget http://nginx.org/download/nginx-1.19.7.tar.gz  && \
    tar xvf nginx-1.19.7.tar.gz   \

	&& wget https://ftp.pcre.org/pub/pcre/pcre-8.38.tar.bz2 && \
	tar xvf pcre-8.38.tar.bz2   \

	&& wget http://www.zlib.net/zlib-1.2.11.tar.gz && \
	tar xvf zlib-1.2.11.tar.gz \

	&& wget https://www.openssl.org/source/OpenSSL_1_1_1b.tar.gz \
	tar xvf OpenSSL_1_1_1b.tar.gz

RUN set -x && \
	&& cd nginx-1.19.7/ && \
	./configure --prefix=/nginx \
				--with-cc-opt="-static -static-libgcc" --with-ld-opt="-static" \
				--with-pcre=../pcre-8.38 --with-zlib=../zlib-1.2.11 \
				--with-openssl=../openssl-OpenSSL_1_1_1b \
				--with-http_ssl_module  \
	&& make     \
	&& make install


FROM alpine:latest
COPY --from=build /nginx  /nginx
WORKDIR  /nginx
EXPOSE 80 443
VOLUME /nginx /nginx/conf /nginx/logs /nginx/html
CMD /nginx/sbin/nginx -c /nginx/conf/nginx.conf -g 'daemon off;'
