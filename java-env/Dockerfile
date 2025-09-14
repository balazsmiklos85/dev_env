FROM alpine:latest

RUN apk update && apk upgrade && apk add --no-cache fish sudo

RUN addgroup -g 1000 bmiklos && \
    adduser -D -s /usr/bin/fish -u 1000 -G bmiklos bmiklos && \
    echo "user ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/bmiklos

USER bmiklos
WORKDIR /home/bmiklos/workspace

CMD ["/usr/bin/fish"]
