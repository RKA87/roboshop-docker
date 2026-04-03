FROM maven:3.5
WORKDIR /app
COPY db .
COPY src .
COPY pom.xml .
RUN mvn clean package
RUN dnf install -y mysql && dnf clean all
RUN mv target/shipping-1.0.jar shipping.jar
ENV CART_ENDPOINT=cart:8080 \
    DB_HOST=mysql
