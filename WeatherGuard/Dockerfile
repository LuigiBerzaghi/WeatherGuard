# Etapa 1: build com Maven
FROM maven:3.9.2-eclipse-temurin-17 AS build
WORKDIR /app
COPY . .
WORKDIR /app/WeatherGuard
RUN mvn clean package -DskipTests

# Etapa 2: imagem leve com JDK apenas
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=build /app/WeatherGuard/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
