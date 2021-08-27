from tomcat:latest
MAINTAINER John Doe <john.doe@gmail.com>
ENV JASPER_VERSION=6.4.0
RUN yum update -y && \
 yum install -y unzip && \
 yum clean all
COPY /resources/TIB_js-jrs_6.4.0_bin.zip /opt/
RUN unzip /opt/TIB_js-jrs_6.4.0_bin.zip -d /opt/ && \
    rm /opt/TIB_js-jrs_6.4.0_bin.zip && \
    mv /opt/jasperreports-server-pro-6.4.0-bin /opt/jasperserver-pro
COPY /resources/default_master.properties /opt/jasperserver-pro/buildomatic/
#Change working directory
WORKDIR /opt/jasperserver-pro/buildomatic
ENV ANT_HOME /opt/jasperserver-pro/apache-ant
ENV PATH $ANT_HOME/bin:$PATH
#Installs JasperReports Server and jasperserver database
RUN ./js-install.sh
#Copy the license file
COPY /resources/jasperserver.license /root
#Change working directory
WORKDIR /opt/tomcat/bin
EXPOSE 8080
CMD ["catalina.sh","run"]