ARG BUILD_FROM=hassioaddons/base:v7.1.1
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

ENV LANG C.UTF-8

# Copy data for add-on
COPY . /
COPY requirements.txt /tmp/

RUN apk add --no-cache gcc
#gcc for uvloop
RUN apk add --no-cache pip3

RUN pip3 install --requirement /tmp/requirements.txt

RUN curl -L -s \
        "https://github.com/mrwiwi/tydom2mqtt/archive/v1.2.2.tar.gz" \
        | tar zxvf - -C /opt/

RUN mv /opt/tydom2mqtt* /opt/tydom2mqtt
RUN chmod a+x /run.sh

# WORKDIR /data

CMD [ "/run.sh" ]
