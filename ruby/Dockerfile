FROM ruby:2.6

# nodejs, yarn
RUN apt-get update \
        && apt-get install -y --no-install-recommends apt-transport-https \
        && curl https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add - \
        && echo "deb https://deb.nodesource.com/node_10.x stretch main" > /etc/apt/sources.list.d/nodesource.list \
        && curl https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - \
        && echo "deb https://dl.yarnpkg.com/debian/ stable main" > /etc/apt/sources.list.d/yarn.list \
        && apt-get update \
        && apt-get install -y --no-install-recommends \
                nodejs \
                yarn \
        && rm -rf /var/lib/apt/lists/*

# make /bin/sh symlink to bash instead of dash
RUN echo "dash dash/sh boolean false" | debconf-set-selections
RUN dpkg-reconfigure -f noninteractive dash

ENV LANG C.utf8
WORKDIR /usr/src/app
