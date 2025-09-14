FROM alpine:latest

RUN apk update && \
    apk upgrade && \
    apk add --no-cache bash curl fish git neovim postgresql postgresql-contrib sudo unzip zip && \
    curl -sS https://starship.rs/install.sh | sh -s -- --yes

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

RUN curl -s "https://get.sdkman.io" | bash
RUN bash -c "source ~/.sdkman/bin/sdkman-init.sh"
RUN bash -c "sdk install java 11.0.14.1-jbr"

CMD ["/usr/bin/fish"]
