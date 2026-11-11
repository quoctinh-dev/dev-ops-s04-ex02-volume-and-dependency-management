# Giai đoạn 1: Build file JAR bằng Gradle
FROM gradle:8.8-jdk21-alpine AS builder
WORKDIR /app
COPY . .
RUN ./gradlew bootJar --no-daemon -x test

# Giai đoạn 2: Runtime JRE 21 nhẹ
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=builder /app/build/libs/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
