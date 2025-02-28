# # Stage 1: Build
# FROM eclipse-temurin:17-jdk AS builder
# WORKDIR /app
# COPY mvnw .
# COPY .mvn .mvn
# COPY pom.xml .
# COPY src src
# RUN ./mvnw package -DskipTests

# # Stage 2: Run
# FROM eclipse-temurin:17-jre
# WORKDIR /app
# COPY --from=builder /app/target/*.jar users-api.jar
# EXPOSE 8083
# ENTRYPOINT ["java", "--add-opens", "java.base/java.lang=ALL-UNNAMED","-jar","users-api.jar"]

# Java Spring Boot Users API
FROM maven:3.8.6-openjdk-11 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn package -DskipTests

FROM openjdk:8-jre-slim
WORKDIR /app
COPY --from=builder /app/target/*.jar ./users-api.jar
EXPOSE 8083
CMD ["java", "-jar", "users-api.jar"]