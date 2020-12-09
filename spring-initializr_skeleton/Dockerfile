FROM openjdk:15 AS builder
COPY . /usr/src/reactive-backend
WORKDIR /usr/src/reactive-backend
RUN ./mvnw clean package

FROM openjdk:15
COPY --from=builder /usr/src/reactive-backend/target/demo-0.0.1-SNAPSHOT.jar /usr/src/reactive-backend/
WORKDIR /usr/src/reactive-backend
EXPOSE 8080
CMD ["java", "-jar", "demo-0.0.1-SNAPSHOT.jar"]