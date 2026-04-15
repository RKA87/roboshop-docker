FROM node:20.20.2-alpine3.23 AS builder
WORKDIR /app
COPY package.json /app
COPY server.js /app
RUN npm install && \
    npm cache clean --force

FROM node:20.20.2-alpine3.23
WORKDIR /app
COPY --from=builder /app /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
RUN chown -R roboshop:roboshop /app
USER roboshop
ENV REDIS_URL=redis://redis:6379 \
    MONGO_URL=mongodb://mongodb:27017/users
ENTRYPOINT ["node"]
CMD ["server.js"]
