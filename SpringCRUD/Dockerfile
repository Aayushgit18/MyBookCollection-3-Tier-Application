# ===============================
# BUILD STAGE
# ===============================
FROM gradle:6.9.4-jdk11 AS build

WORKDIR /app
COPY . .

RUN gradle clean bootJar --no-daemon

# ===============================
# RUNTIME STAGE
# ===============================
FROM eclipse-temurin:11-jre-alpine

WORKDIR /app

COPY --from=build /app/build/libs/*.jar app.jar

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]

