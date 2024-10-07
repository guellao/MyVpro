FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone -b vp-docker https://github.com/guellao/MyVpro.git
RUN cd MyVpro && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Mhamed"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE MyVpro/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
