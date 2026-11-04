FROM maven:3.9.16-eclipse-temurin-21 AS BUILD_IMAGE
COPY . /app
WORKDIR /app
RUN mvn install

FROM tomcat:10.1.60-jre21-temurin-noble
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE /app/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]