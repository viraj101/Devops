

FROM debian:stretch-slim

ARG IM_VERSION=7.0.10-9
RUN apt-get -y update && \
    apt-get -y upgrade && \
    apt-get -y install git make gcc pkg-config autoconf && \
    apt-get -y install libpng16-16 libpng-dev libjpeg62-turbo libjpeg62-turbo-dev libwebp6 libwebp-dev libgomp1 libwebpmux2 libwebpdemux2 ghostscript && \
    git clone https://github.com/ImageMagick/ImageMagick.git && \
    cd ImageMagick && git checkout ${IM_VERSION} && \
    ./configure && make && make install && \
    ldconfig /usr/local/lib && \
    apt-get remove --autoremove --purge -y gcc make git autoconf pkg-config libpng-dev libjpeg62-turbo-dev libwebp-dev && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /ImageMagick
    apt-get- y openjdk-11-jre openjdk-11-jdk
ENTRYPOINT ["convert"]
WORKDIR /apps
COPY . /apps
COPY searcherservice.jar /apps
EXPOSE 8190
#CMD ["java", "-jar", "searcherservice.jar"]

CMD java -jar searcherservice.jar --spring.config.location=externalConfig/application.properties


