FROM golang:latest
WORKDIR /app
COPY main.go .
RUN go mod init dispatch
RUN go get
RUN go build
ENV AMQP_HOST=rabbitmq \
    AMQP_USER=roboshop \
    AMQP_PASS=roboshop123
ENTRYPOINT [ "/app/dispatch" ]
