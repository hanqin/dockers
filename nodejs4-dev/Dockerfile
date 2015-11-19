FROM ubuntu:trusty

RUN apt-get upgrade -yq
RUN sudo rm /var/lib/apt/lists/* -rvf
RUN sudo apt-get update -y
RUN apt-get install -yq \
    curl \
    git \
    vim \
    build-essential \
    python-software-properties \
    python \
    g++ \
    make

# Install vimified
RUN curl -L https://raw.githubusercontent.com/hanqin/vimified/master/install.sh | sh

# Install git-extras
RUN curl -sSL http://git.io/git-extras-setup | sudo bash /dev/stdin

# Install alias
RUN curl -L https://raw.githubusercontent.com/hanqin/git-alias/master/install.sh | sh

# Credential store
RUN git config --global credential.helper cache
RUN git config --global credential.helper 'cache --timeout=3600'

# Install nodejs4
RUN curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
RUN sudo apt-get install -y nodejs

# Logging
RUN node -v && npm -v

# Prepare tools
RUN npm --registry=https://registry.npm.taobao.org install -g \
    bunyan \
    nodemon \
    gulp \
    cnpm

# Workdir
ENV APP /app
RUN mkdir $APP
VOLUME $APP
WORKDIR $APP

