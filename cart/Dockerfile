# Using MultiStage build process to reduce the image size and attack surface
# Builder stage to install the code and node modules only

FROM node:20.20.2-alpine3.23 AS builder
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install


FROM node:20.20.2-alpine3.23
WORKDIR /app
EXPOSE 8080
# Copying only the necessary files from the builder stage to reduce the image size and attack surface
COPY --from=builder /app /app
ENV REDIS_HOST='redis' \
    CATALOGUE_HOST='catalogue' \
    CATALOGUE_PORT='8080'
ENTRYPOINT ["node"]
CMD [ "server.js" ]



# FROM node:20
# EXPOSE 8080
# WORKDIR /app
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV REDIS_HOST='redis' \
#     CATALOGUE_HOST='catalogue' \
#     CATALOGUE_PORT='8080'
# ENTRYPOINT ["node"]
# CMD [ "server.js" ]

