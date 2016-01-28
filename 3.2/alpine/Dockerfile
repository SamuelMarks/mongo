FROM alpine:3.3

# add our user and group first to make sure their IDs get assigned consistently, regardless of whatever dependencies get added
RUN addgroup -S mongodb && adduser -S -G mongodb mongodb

RUN echo @testing http://nl.alpinelinux.org/alpine/edge/testing >> /etc/apk/repositories \
    && apk update \
		&& apk add mongodb@testing

RUN mkdir -p /data/db && chown -R mongodb:mongodb /data
VOLUME /data
WORKDIR /data

# See https://docs.mongodb.org/manual/reference/default-mongodb-port/
EXPOSE 27017
EXPOSE 28017

CMD [ "mongod" ]
