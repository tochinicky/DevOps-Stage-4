# users/Dockerfile
FROM maven:3.8.6-openjdk-11 as build
WORKDIR /app
COPY . .
RUN mvn clean package

FROM openjdk:11-jre-slim
COPY --from=build /app/target/*.jar users-api.jar
EXPOSE 8083
CMD ["java", "-jar", "users-api.jar"]