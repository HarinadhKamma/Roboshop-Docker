FROM node:24.12.0-alpine3.21 AS build
WORKDIR /opt/server
COPY *.json .
COPY *.js .
RUN npm install



FROM node:24.12.0-alpine3.21
WORKDIR /opt/server
EXPOSE 8080
COPY --from=build /opt/server /opt/server
# Create a group and user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
    chown -R roboshop:roboshop /opt/server
USER roboshop
LABEL com.project="roboshop" \
    component="catalogue" \
    craetedby="hari"
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue" 
CMD ["server.js"]
ENTRYPOINT [ "node" ]