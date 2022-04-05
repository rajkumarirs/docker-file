ROM centos
MAINTAINER rajkumar rajkumar.irs555@gmail.com
RUN sed-i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed-i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.cent
RUN mkdir /opt/Tomcat
WORKDIR /opt/Tomcat
RUN curl -0 https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.59/bin/apache-t
RUN tar -xvzf apache*.tar.gz
RUN mv apache-tomcat-9.0.59/* /opt/Tomcat
RUN yum update -y
RUN yum install -y java
RUN yum install wget -Y
RUN yum install vim -Y
RUN yum install git -Y
RUN yum install maven -y
RUN java -version
WORKDIR /opt/Tomcat/webapps
COPY ./jenkins.war/opt/Tomcat/webapps
EXPOSE 8080
CMD ["/opt/Tomcat/bin/startup.sh", "run"] 
