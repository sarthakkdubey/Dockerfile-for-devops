#java version runtime
FROM eclipse-temurin:17-jdk-alpine

#working dir
WORKDIR /app

#copy traget file from source
COPY target/*.jar app.jar

#exposed port
EXPOSE 8080

#entrypoints to run the application
ENTRYPOINT ["java","-jar","app.jar"]
