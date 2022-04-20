ARG BUILD_FROM
FROM $BUILD_FROM

RUN \
    apk add --no-cache \
        py3-pip \
        python3

# Copy data
COPY rootfs /