FROM node:20.20.2-alpine3.23 AS builder
WORKDIR /app
COPY server.js /app
COPY package.json /app
RUN npm install && \
    npm install -g pm2 && \
    npm cache clean --force


FROM node:20.20.2-alpine3.23
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
COPY --from=builder /app /app
RUN chown -R roboshop:roboshop /app
USER roboshop
# Giving the ENV variables from docker-compose file using environment
# ENV MONGO=true" \
#     MONGO_URL=mongodb://mongodb:27017/catalogue"
ENTRYPOINT ["node"]
CMD ["server.js"]