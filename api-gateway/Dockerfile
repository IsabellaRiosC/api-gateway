# ── Stage 1: Build ──────────────────────────────────────────────
FROM maven:3.9-eclipse-temurin-17 AS builder
WORKDIR /build

# Copiar archivos de configuración y pom primero para aprovechar caché
COPY pom.xml checkstyle.xml ./
RUN mvn dependency:go-offline -B || true

# Copiar el código fuente y compilar
COPY src ./src
RUN mvn clean package -DskipTests -B

# ── Stage 2: Runtime ─────────────────────────────────────────────
FROM eclipse-temurin:17-jre
WORKDIR /app
COPY --from=builder /build/target/api-gateway-1.0.0.jar app.jar
EXPOSE 7000
ENTRYPOINT ["java", "-jar", "/app/app.jar"]
