FROM node:20
WORKDIR /app
COPY package.json .
COPY server.js .
RUN npm install
EXPOSE 8080
ENTRYPOINT ["node"]
CMD ["server.js"]
ENV MONGO_URL="mongodb://mongodb:27017/users"
    REDIS_URL="redis://redis:6379"