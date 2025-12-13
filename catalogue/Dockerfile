FROM node:24.12.0-alpine3.22 AS build
WORKDIR /opt/server
COPY *.json .
COPY *.js .
RUN npm install
CMD ["node","server.js"]


FROM node:24.12.0-alpine3.22
WORKDIR /opt/server
COPY --from=build /opt/server /opt/server
# Create a group and user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
USER roboshop
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue" 
CMD ["node","server.js"]