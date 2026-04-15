FROM maven:3.9.9-eclipse-temurin-17 AS build

WORKDIR /workspace
# Build with the repository root as context:
# docker build -f gameoflife-web/Dockerfile .
COPY . .
RUN mvn -pl gameoflife-web -am package -DskipTests

FROM tomcat:9.0-jre17-temurin

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=build /workspace/gameoflife-web/target/gameoflife.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
