FROM openjdk:14 AS builder
COPY . /usr/src/reactive-backend
WORKDIR /usr/src/reactive-backend
RUN ./mvnw clean package

FROM openjdk:14
COPY --from=builder /usr/src/reactive-backend/target/reactive-web-1.0.0-SNAPSHOT.jar /usr/src/reactive-backend/
COPY --from=builder /usr/src/reactive-backend/wait-for-it.sh /usr/src/reactive-backend/wait-for-it.sh
WORKDIR /usr/src/reactive-backend
RUN ls
RUN chmod +x /usr/src/reactive-backend/wait-for-it.sh
EXPOSE 8080
CMD ./wait-for-it.sh mongo:27017 -t 180 && java -jar reactive-web-1.0.0-SNAPSHOT.jar