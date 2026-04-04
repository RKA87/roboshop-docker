# FROM redhat/ubi9
# RUN adduser -D roboshop
# USER roboshop
# WORKDIR /app
# ADD https://roboshop-artifacts.s3.amazonaws.com/catalogue-v3.zip .
# RUN unzip -o catalogue-v3.zip && rm -f catalogue-v3.zip

FROM node:20
EXPOSE 8080
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
ENTRYPOINT ["node"]
CMD [ "server.js" ]