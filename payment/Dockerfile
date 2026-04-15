FROM python:3.9.25-alpine3.22 AS builder
WORKDIR /app
RUN apk add --no-cache build-base linux-headers pcre-dev
COPY payment.ini /app
COPY *.py /app
COPY requirements.txt /app
RUN pip3.9 install --prefix=/install -r requirements.txt


FROM python:3.9.25-alpine3.22
EXPOSE 8080
WORKDIR /app
RUN apk add --no-cache pcre-dev
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
#here /app is source and other /app is deestination... files to copied from builder image to current image
COPY --from=builder /app /app
COPY --from=builder /install /usr/local
RUN chown -R roboshop:roboshop /app
USER roboshop
ENV CART_HOST=cart \
    CART_PORT=8080 \
    USER_HOST=user \
    USER_PORT=8080 \
    AMQP_HOST=rabbitmq \
    AMQP_USER=roboshop \
    AMQP_PASS=roboshop123
ENTRYPOINT ["/usr/local/bin/uwsgi"]
CMD [ "--ini", "payment.ini" ]
