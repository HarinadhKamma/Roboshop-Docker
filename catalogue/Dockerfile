FROM node:24.12.0-alpine3.22
WORKDIR /opt/server
COPY *.json .
COPY *.js .
RUN npm install
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue" 
CMD ["node","server.js"]