# Using a minimal image of Nodejs with alpine linux to reduce the image size and attack surface
FROM node:20.20.2-alpine3.23 AS builder
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install


FROM node:20.20.2-alpine3.23
EXPOSE 8080
WORKDIR /app
COPY --from=builder /app /app
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
ENTRYPOINT ["node"]
CMD [ "server.js" ]



# FROM node:20
# EXPOSE 8080
# WORKDIR /app
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# ENTRYPOINT ["node"]
# CMD [ "server.js" ]