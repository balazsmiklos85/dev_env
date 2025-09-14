FROM alpine:latest

RUN apk update && \
    apk upgrade && \
    apk add --no-cache curl fish sudo && \
    curl -sS https://starship.rs/install.sh | sh -s -- --yes

RUN addgroup -g 1000 bmiklos && \
    adduser -D -s /usr/bin/fish -u 1000 -G bmiklos bmiklos && \
    echo "user ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/bmiklos

USER bmiklos
WORKDIR /home/bmiklos/workspace

CMD ["/usr/bin/fish"]
