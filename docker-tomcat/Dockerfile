FROM alpine
#FROM ubuntu
RUN apt-get update -y \
    && apt-get install openjdk-8-jre openjdk-8-jdk maven wget vim curl -y
RUN export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64

ENV TOMCAT_MAJOR=8 \
    TOMCAT_VERSION=8.5.37 \
    CATALINA_HOME=/opt/tomcat
RUN curl -jkSL -o /tmp/apache-tomcat.tar.gz http://archive.apache.org/dist/tomcat/tomcat-${TOMCAT_MAJOR}/v${TOMCAT_VERSION}/bin/apache-tomcat-${TOMCAT_VERSION}.tar.gz && \
    gunzip /tmp/apache-tomcat.tar.gz && \
    tar -C /opt -xf /tmp/apache-tomcat.tar && \
    ln -s /opt/apache-tomcat-$TOMCAT_VERSION $CATALINA_HOME
RUN mkdir -p /opt
EXPOSE 8080

COPY startup.sh /opt/startup.sh
COPY sample.war /opt/tomcat/webapps
ENTRYPOINT /opt/startup.sh

WORKDIR $CATALINA_HOME

