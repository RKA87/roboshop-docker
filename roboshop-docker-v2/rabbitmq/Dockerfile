FROM rabbitmq:3.13
RUN rabbitmqctl add_user roboshop roboshoppassword
RUN rabbitmqctl set_permissions -p / roboshop ".*" ".*" ".*"