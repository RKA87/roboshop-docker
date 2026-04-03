FROM python:3.11
WORKDIR /app
COPY payment.ini .
COPY rabbitmq.py .
COPY payment.py .
COPY requirements.txt .
RUN pip install
ENV CART_HOST=cart \
    CART_PORT=8080 \
    USER_HOST=user \
    USER_PORT=8080 \
    AMQP_HOST=rabbitmq \
    AMQP_USER=roboshop \
    AMQP_PASS=roboshop123
ENTRYPOINT ["/usr/local/bin/uwsgi"]
CMD [ "--ini", "payment.ini" ]