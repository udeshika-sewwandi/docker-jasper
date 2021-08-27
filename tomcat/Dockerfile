FROM java:latest
MAINTAINER John Doe <john.doe@gmail.com>
ENV TOMCAT_MAJOR=8 \
    TOMCAT_VERSION=8.5.70
ENV CATALINA_HOME /opt/tomcat
ENV PATH $CATALINA_HOME/bin:$PATH
#ENV TOMCAT_TGZ_URL https://www.apache.org/dist/tomcat/tomcat-$TOMCAT_MAJOR/v$TOMCAT_VERSION/bin/apache-tomcat-$TOMCAT_VERSION.tar.gz
COPY /resources/apache-tomcat-${TOMCAT_VERSION}.tar.gz /opt/
RUN tar -xvf /opt/apache-tomcat-${TOMCAT_VERSION}.tar.gz --directory /opt/ && \
    mv /opt/apache-tomcat-${TOMCAT_VERSION} /opt/tomcat
EXPOSE 8080
CMD ["catalina.sh","run"]