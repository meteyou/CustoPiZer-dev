# syntax=docker/dockerfile:1
ARG VERSION="bookworm"
ARG RELEASE_NAME=${VERSION}-backports
FROM debian:${RELEASE_NAME}

ENV RELEASE_NAME=${RELEASE_NAME}
ENV PACKAGES="binfmt-support build-essential lsof sudo util-linux fdisk"
ENV BPO="qemu-system qemu-user-static"

RUN set -ex \
    && apt-get update \
    && apt-get install --no-install-recommends --yes ${PACKAGES} \
    && apt-get install --no-install-recommends --yes -t ${RELEASE_NAME} ${BPO} \
    && apt autoremove \
    && rm -rf /var/lib/apt/lists/*

COPY . /CustoPiZer

ENTRYPOINT [ "/bin/bash" ]
CMD [ "/CustoPiZer/customize" ]
