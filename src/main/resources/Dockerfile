# 1️⃣ build stage
FROM gradle:8.14-jdk21 AS builder

WORKDIR /build
COPY . .

RUN gradle build -x test

# 2️⃣ run stage
FROM eclipse-temurin:21-jdk

WORKDIR /app
COPY --from=builder /build/build/libs/*.jar app.jar

ENTRYPOINT ["java","-jar","app.jar"]