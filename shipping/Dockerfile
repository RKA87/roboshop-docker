FROM maven:3.9.14
EXPOSE 8080
WORKDIR /app
COPY src ./src
COPY pom.xml .
RUN mvn clean package
RUN dnf install -y mysql && dnf clean all
RUN mv target/shipping-1.0.jar shipping.jar
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
ENTRYPOINT ["java", "-jar", "shipping.jar"]
