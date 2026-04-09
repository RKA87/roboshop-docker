FROM node:20-alpine AS builder
WORKDIR /app
COPY package.json .
COPY server.js .
RUN npm install


    
FROM node:20-alpine
WORKDIR /app
COPY --from=builder /app .
EXPOSE 8080
RUN adduser -u roboshop -
ENTRYPOINT ["node"]
CMD ["server.js"]
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"