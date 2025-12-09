FROM maven:3.9-eclipse-temurin-17-alpine AS builder

WORKDIR /app/voting

COPY pom.xml .

COPY src ./src

RUN mvn clean package -DskipTests

FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app/voting

COPY --from=builder /app/voting/target/voting-0.0.1-SNAPSHOT.jar voting.jar

CMD ["java", "-jar", "voting.jar"]