FROM golan:latest
WORKDIR /app
COPY main.go .
RUN go mod init dispatch \
    && go get \
    && go build
ENV AMQP_HOST="rabbitmq"
    AMQP_USER="roboshop"
    AMQP_PASSWORD="roboshop123"
CMD ["/app/dispatch"]
EXPOSE 8080