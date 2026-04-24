FROM golang:alpine3.22 AS builder
WORKDIR /app
COPY main.go /app
RUN go mod init dispatch && \
    go mod tidy && \
    go build -o dispatch

FROM alpine:3.22
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
COPY --from=builder /app/dispatch /app/dispatch
RUN chown -R roboshop:roboshop /app
USER roboshop
ENV AMQP_HOST=rabbitmq \
    AMQP_USER=roboshop \
    AMQP_PASS=roboshop123
ENTRYPOINT ["/app/dispatch"]