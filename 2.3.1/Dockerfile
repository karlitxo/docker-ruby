FROM ubuntu:14.04

ENV LANG en_US.UTF-8
ENV CONFIGURE_OPTS --disable-install-rdoc --enable-shared
ENV DEBIAN_FRONTEND noninteractive

# --no-install-recommends to avoid installing fuse (unsupported in docker < 1.0)
RUN apt-get update && \
    apt-get install --no-install-recommends -y wget build-essential ca-certificates autoconf bison libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev && \
    apt-get autoremove && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN mkdir ruby-build && \
    wget -qO- https://github.com/rbenv/ruby-build/archive/v20160426.tar.gz | \
    tar xz -C ruby-build/ --strip-components 1 && \
    cd ruby-build && \
    ./bin/ruby-build 2.3.1 /usr/local && rm -rf ruby-build

RUN gem install bundler 

WORKDIR /rails_app
