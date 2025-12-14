FROM node:24.12.0-alpine3.22 AS build
WORKDIR /opt/server
COPY *.json .
COPY *.js .
RUN npm install

FROM node:24.12.0-alpine3.22
WORKDIR /opt/server
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
LABEL com.project="roboshop" \
    component="user" \
    craetedby="hari"
ENV MONGO="true" \
    REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users" 
COPY --from=build --chown=robohop:robohsop /opt/server /opt/server/
USER  robohop
CMD ["server.js"]
ENTRYPOINT [ "node" ]