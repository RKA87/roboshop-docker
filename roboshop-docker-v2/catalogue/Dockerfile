FROM node:20-alpine AS builder
WORKDIR /app
COPY package.json .
COPY server.js .
COPY db .
RUN npm install


    
FROM node:20-alpine
WORKDIR /app
COPY --from=builder /app .
ENTRYPOINT ["node"]
CMD ["server.js"]
ENV MONGO_URL="mongodb://mongodb:27017/catalogue" \
    MONGO="true"
EXPOSE 8080