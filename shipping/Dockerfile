FROM maven:3.9.11 AS build
WORKDIR /opt/server
COPY pom.xml .
COPY src ./src
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar 


FROM eclipse-temurin:17-jre-alpine
RUN  addgroup -S roboshop && adduser -S roboshop -G roboshop
COPY --from=build --chown=robohop:robohop /opt/server/shipping.jar .
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
USER roboshop
CMD [ "java","-jar","shipping.jar" ]