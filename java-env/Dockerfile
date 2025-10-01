FROM alpine:latest

RUN apk update
RUN apk upgrade
RUN apk add --no-cache fish \
    git \
    neovim \
    openjdk21 \
    openssh-client \
    python3 \
    starship \
    starship-fish-completion \
    sudo

RUN addgroup -g 1000 bmiklos && \
    adduser -D -s /usr/bin/fish -u 1000 -G bmiklos bmiklos && \
    echo "user ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/bmiklos

RUN mkdir -p /home/bmiklos/.config
RUN mkdir -p /tmp/config-repo
RUN git clone https://github.com/balazsmiklos85/dotfiles.git /tmp/config-repo
RUN cp -r /tmp/config-repo/* /home/bmiklos/.config/
RUN rm -rf /tmp/config-repo

RUN chown -R bmiklos:bmiklos /home/bmiklos/.config

USER bmiklos
WORKDIR /home/bmiklos/workspace

CMD ["/usr/bin/fish"]
