FROM alpine:3.8

ENV LANG 'en_US.UTF-8'
ENV LC_LANG 'en_US.UTF-8'
ENV LC_ALL 'en_US.UTF-8'
ENV PYTHONIOENCODING "utf-8"
ENV HOME /
ENV PYENV_ROOT $HOME/.pyenv
ENV PATH $PYENV_ROOT/shims:$PYENV_ROOT/bin:$PATH

COPY . /app

RUN rm -rf /var/cache/apk/*
RUN apk add --no-cache --virtual=build-deps build-base \
    openssl-dev \
    py-pip \
    git \
    tzdata \
    musl \
    bzip2-dev \
    gfortran \
    linux-headers \
    make \
    openblas-dev \
    python3-dev \
    readline-dev \
    sqlite-dev \
    zlib-dev
RUN apk add --no-cache bash \
    python3

RUN cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
RUN git clone https://github.com/yyuu/pyenv.git ~/.pyenv
RUN pyenv install 3.6.3
RUN pyenv global 3.6.3
RUN apk del --no-cache build-deps
WORKDIR /app/src