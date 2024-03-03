FROM openjdk:11 AS BUILD_IMAGE
LABEL "project"="vprofile"
LABEL "Author"="Abere"
RUN apt update && apt install maven -y
RUN git clone https://github.com/aberekerehu/devops/tree/containers
RUN cd devops && git checkout docker && mvn install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE devops/tagrget/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh","run"]