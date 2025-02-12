# syntax=docker/dockerfile:1
ARG VERSION="bookworm"
FROM debian:${VERSION}-backports

ENV VERSION=${VERSION}
ENV PACKAGES="binfmt-support build-essential lsof sudo util-linux fdisk"
ENV BPO="qemu-system qemu-user-static"
ENV BPO_TARGET="${VERSION}-backports"

RUN set -ex \
    && apt-get update \
    && apt-get install --no-install-recommends --yes ${PACKAGES} \
    && apt-get install --no-install-recommends --yes -t "${BPO_TARGET}" ${BPO} \
    && apt autoremove \
    && rm -rf /var/lib/apt/lists/*

COPY . /CustoPiZer

ENTRYPOINT [ "/bin/bash" ]
CMD [ "/CustoPiZer/customize" ]
