ARG BUILD_FROM
FROM $BUILD_FROM

RUN \
    apk add --no-cache --virtual .build-dependencies \
        build-base \
        libffi-dev \
    && apk add --no-cache \
            py3-pip \
            python3-dev \
            py3-numpy \
            py3-pandas \
            py3-scikit-learn \
            mariadb-connector-c-dev

# Copy data
COPY rootfs /
RUN pip3 install thesillyhome
COPY appdaemon /appdaemon
