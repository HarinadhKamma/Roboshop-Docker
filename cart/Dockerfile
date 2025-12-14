FROM node:24.12.0-alpine3.22 AS build
WORKDIR /opt/server
COPY *.json .
COPY *.js .
RUN npm install


FROM node:24.12.0-alpine3.22 
EXPOSE 8080
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080" 
LABEL com.project="roboshop" \
      component="cart" \
      craetedby="hari"
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
COPY --from=build --chown=robohop:roboshop /opt/server /opt/server
USER robohop
CMD ["node","server.js"]