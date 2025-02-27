# Stage 1: Build the application (using Maven and OpenJDK 8)
FROM maven:3.8.6-openjdk-11 AS build

WORKDIR /app

COPY pom.xml .
COPY mvnw .
COPY .mvn .mvn

COPY src ./src

RUN mvn package -DskipTests

# Stage 2: Create the runtime image (using OpenJDK 8 JRE for minimal size)
FROM openjdk:8-jre-slim

WORKDIR /app

COPY --from=build /app/target/*.jar ./users-api.jar

ENV SERVER_PORT=8083

EXPOSE ${SERVER_PORT}

RUN useradd -m -r appuser && \
    chown appuser:appuser /app
USER appuser

CMD ["java", "-jar", "users-api.jar"]