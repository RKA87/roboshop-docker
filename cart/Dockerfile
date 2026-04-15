FROM node:20.20.2-alpine3.23 AS builder
WORKDIR /app
COPY package.json /app
COPY server.js /app
RUN npm install && \
    npm cache clean --force

FROM node:20.20.2-alpine3.23
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
COPY --from=builder /app /app
RUN chown -R roboshop:roboshop /app
USER roboshop
ENV REDIS_HOST=redis \
    CATALOGUE_HOST=catalogue \
    CATALOGUE_PORT=8080
ENTRYPOINT ["node"]
CMD [ "server.js" ]