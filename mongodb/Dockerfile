FROM mongo:7
# Replace "bindIp: 127.0.0.1" with "bindIp: 0.0.0.0"
RUN sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/g' /etc/mongod.conf
COPY *.js /docker-entrypoint-initdb.d/