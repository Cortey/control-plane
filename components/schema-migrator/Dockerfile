FROM alpine:3.14.2
LABEL source=git@github.com:kyma-project/control-plane.git

ARG MIGRATE_VER=4.14.1

WORKDIR /migrate

RUN apk --no-cache add bash>=5.1.8-r0 --repository=http://dl-cdn.alpinelinux.org/alpine/edge/main
RUN apk --no-cache add postgresql-client
RUN apk --no-cache add --update curl --repository=http://dl-cdn.alpinelinux.org/alpine/v3.14/main
RUN wget https://github.com/golang-migrate/migrate/releases/download/v${MIGRATE_VER}/migrate.linux-amd64.tar.gz -O - | tar -xz
RUN mv migrate.linux-amd64 /usr/local/bin/migrate

COPY ./migrations/ ./migrations
COPY ./run.sh ./run.sh

ENTRYPOINT ["./run.sh"]
