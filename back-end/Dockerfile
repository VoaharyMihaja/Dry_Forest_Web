FROM maven:3.9.9-eclipse-temurin-17 AS build

WORKDIR /workspace

# Copy only what is needed for a Maven build
COPY pom.xml ./
COPY src ./src

# Build the application inside the container
RUN mvn -DskipTests package

FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app

# Copy the built jar from the build stage
COPY --from=build /workspace/target/*.jar app.jar

EXPOSE 8081

ENTRYPOINT ["java", "-jar", "app.jar"]