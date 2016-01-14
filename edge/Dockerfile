FROM ubuntu

RUN sudo apt-get -y update

RUN sudo apt-get -y install \
	build-essential \
	libpcre3 \
	libpcre3-dev \
	libssl-dev \
	wget \
	unzip \
	software-properties-common 

RUN echo | add-apt-repository ppa:mc3man/trusty-media && apt-get update && apt-get -y install ffmpeg gstreamer0.10-ffmpeg

RUN mkdir /usr/src/nginx && cd /usr/src/nginx && \
	wget http://nginx.org/download/nginx-1.9.5.tar.gz && \
	wget https://github.com/arut/nginx-rtmp-module/archive/master.zip && \
	tar -zxvf nginx-1.9.5.tar.gz && \
	unzip master.zip

RUN cd /usr/src/nginx/nginx-1.9.5 && \
	./configure --with-http_ssl_module --add-module=../nginx-rtmp-module-master && \
	make && \
	sudo make install

ADD nginx.conf /usr/local/nginx/conf/nginx.conf
RUN echo "\ndaemon off;" >> /usr/local/nginx/conf/nginx.conf

CMD sudo /usr/local/nginx/sbin/nginx

EXPOSE 1935
