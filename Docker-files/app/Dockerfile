FROM maven:3.9.9-eclipse-temurin-21-jammy AS BUILD_IMAGE
RUN https://github.com/aruhtas/Vprofile-Project.git
RUN cd Vprofile-Project && git checkout containers && mvn install


FROM tomcat:10-jdk21
LABEL Project="Vprofile"
LABEL Author="Dev"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]

