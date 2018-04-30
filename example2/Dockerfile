FROM centos:centos7

MAINTAINER zeko han (mulan101@gmail.com)

RUN yum update -y
RUN yum install wget -y

# Java installation.
RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u141-b15/336fa29ff2bb4ef291e347e091f7f4a7/jdk-8u141-linux-x64.rpm
RUN yum install -y jdk-8u141-linux-x64.rpm


# Tomcat 8 installation
RUN wget -O /tmp/apache-tomcat-8.5.30.tar.gz http://apache.tt.co.kr/tomcat/tomcat-8/v8.5.30/bin/apache-tomcat-8.5.30.tar.gz
RUN cd /usr/local && tar xzf /tmp/apache-tomcat-8.5.30.tar.gz
RUN ln -s /usr/local/apache-tomcat-8.5.30 /usr/local/tomcat

# Download Maven
RUN wget -O /tmp/apache-maven-3.1.1-bin.tar.gz http://ftp.jaist.ac.jp/pub/apache/maven/maven-3/3.1.1/binaries/apache-maven-3.1.1-bin.tar.gz
RUN cd /usr/local && tar xzf /tmp/apache-maven-3.1.1-bin.tar.gz
RUN ln -s /usr/local/apache-maven-3.1.1 /usr/local/maven

# Environment variables
ENV JAVA_HOME /usr/java/latest
ENV CATALINA_HOME /usr/local/tomcat
ENV MAVEN_HOME /usr/local/maven

# Clone the application itself
RUN yum install git -y

# tomcat start
CMD $CATALINA_HOME/bin/startup.sh && tail -F /usr/local/tomcat/logs/catalina.out

# Forward HTTP ports
EXPOSE 8080