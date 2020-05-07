
FROM openjdk:11-jre-slim

#MAINTAINER prudviraj
#RUN apt-get update -y && apt-get install apt-utils -y && apt-get install imagemagick -y && apt-get install build-essential -y && apt-get install curl -y 
RUN apt-get update && apt-get install -y apt-utils && apt-get install -y curl
RUN apt-get update -y && apt-get install build-essential -y && apt-get install wget -y && wget https://www.imagemagick.org/download/ImageMagick.tar.gz && tar xvzf ImageMagick.tar.gz && cd ImageMagick-7.0.10-10 && ./configure && make && make install && ldconfig /usr/local/lib && magick -version && \
    apt-get -y install libpng16-16 libpng-dev libjpeg62-turbo libjpeg62-turbo-dev libwebp6 libwebp-dev libgomp1 ghostscript

WORKDIR /apps
COPY . /apps
COPY searcherservice.jar /apps
EXPOSE 8190
#CMD ["java", "-jar", "searcherservice.jar"]
RUN pwd 
RUN cd /
RUN cd /ImageMagick-7.0.10-10
RUN ./configure --enable-shared --with-png=yes && ./configure --enable-shared --with-jpg=yes

CMD java -jar searcherservice.jar --spring.config.location=externalConfig/application.properties


