# TODO: change from ffmpeg 5.1+ to yt-dlp/FFmpeg
FROM jrottenberg/ffmpeg:5.1-alpine as ffmpeg

FROM alpine:3.16 as sanjuuni

# TODO: use the same ffmpeg for sanjuuni
RUN set -x \
    && apk add --no-cache --update git g++ zlib-dev poco-dev make ffmpeg-dev \
    && git clone https://github.com/MCJack123/sanjuuni.git

WORKDIR /sanjuuni

RUN set -x \
    && ./configure \
    && make

FROM mcr.microsoft.com/vscode/devcontainers/base:alpine-3.16

RUN set -x \
    && apk add --no-cache --update python3 py3-pip gcc libc-dev \
    # ffmpeg requirements
    libgcc libstdc++ ca-certificates libcrypto1.1 libssl1.1 libgomp expat \
    # sanjuuni requirements
    poco \
    # utils
    make \
    && pip install --no-cache-dir --upgrade pip \
    # python-is-python3
    && ln -sf python3 /usr/bin/python

# add ffmpeg
COPY --from=ffmpeg /usr/local /usr/local

# add sanjuuni
COPY --from=sanjuuni /sanjuuni/sanjuuni /usr/local/bin

# Use ffmpeg libs
ENV LD_LIBRARY_PATH=/usr/local/lib:/usr/local/lib64
