FROM maven:3.9.14 AS builder
WORKDIR /app
COPY pom.xml /app
COPY src /app/src
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar


FROM eclipse-temurin:17-jre-alpine
EXPOSE 8080
WORKDIR /app
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
COPY --from=builder /app /app
RUN chown -R roboshop:roboshop /app
USER roboshop
ENV CART_ENDPOINT=cart:8080 \
    DB_HOST=mysql
ENTRYPOINT [ "java" ]
CMD [ "-jar", "shipping.jar" ]
