FROM maven:3.8.4-jdk-11-slim as builder

WORKDIR .
COPY . .

RUN mvn dependency:resolve

RUN mvn package

FROM openjdk:11-jre-slim

COPY --from=builder /target/worker-jar-with-dependencies.jar .

EXPOSE 80

CMD [ "java", "-jar", "worker-jar-with-dependencies.jar"]
