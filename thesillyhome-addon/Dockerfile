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
    mariadb-connector-c-dev \
    && pip3 install thesillyhome==0.2.8 \
    && pip3 install appdaemon==4.2.1 \
    && apk del .build-dependencies

# Copy data
COPY rootfs /
COPY appdaemon /appdaemon

# # dev stuff
# COPY thesillyhome /thesillyhome
# COPY thesillyhome/src/thesillyhome/model_creator/data_cache/options.json /data/options.json
# RUN pip3 install -U setuptools
# RUN python3 /thesillyhome/setup.py develop

