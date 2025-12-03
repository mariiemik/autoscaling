# 1. Build stage
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app
COPY pom.xml .
RUN mvn -q -e -DskipTests dependency:go-offline
COPY src ./src
RUN mvn -q -e -DskipTests package

# 2. Run stage (минимальный JRE)
FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar

# уменьшение памяти JVM
ENV JAVA_OPTS="-Xms128m -Xmx256m"

ENTRYPOINT ["sh", "-c", "java $JAVA_OPTS -jar app.jar"]
