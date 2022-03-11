FROM maven:latest as maven

COPY ./src ./src

RUN mvn clean install && \
    mvn package

FROM openjdk:19-jdk-alpine

WORKDIR /app

COPY --from=maven target/botify-*.jar ./app.jar

CMD ["java", "-jar", "./app.jar"]