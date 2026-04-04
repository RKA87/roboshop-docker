FROM python:3.9
EXPOSE 8080
WORKDIR /app
COPY requirements.txt .
RUN pip install -r rquirements.txt
COPY payment.ini .
COPY *.py .
ENV CART_HOST='cart' \
    CART_PORT='8080' \
    USER_HOST='user' \
    USER_PORT='8080' \
    AMQP_HOST='rabbitmq' \
    AMQP_USER='roboshop' \
    AMQP_PASS='roboshop123'
ENTRYPOINT ["/usr/local/bin/uwsgi"]
CMD [ "--ini", "payment.ini" ]