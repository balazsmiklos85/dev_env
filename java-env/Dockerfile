FROM alpine:latest

RUN apk update && \
    apk upgrade && \
    apk add --no-cache bash curl fish git neovim sudo unzip zip && \
    curl -sS https://starship.rs/install.sh | sh -s -- --yes

RUN addgroup -g 1000 bmiklos && \
    adduser -D -s /usr/bin/fish -u 1000 -G bmiklos bmiklos && \
    echo "user ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/bmiklos

USER bmiklos
WORKDIR /home/bmiklos/workspace

RUN curl -s "https://get.sdkman.io" | bash
RUN bash -c "source ~/.sdkman/bin/sdkman-init.sh && \
    sdk install java 11.0.14.1-jbr"

CMD ["/usr/bin/fish"]
