ARG DOCKER_REGISTRY_URL
ARG DOCKER_IMAGE
ARG ONEC_VERSION
FROM ${DOCKER_REGISTRY_URL}/${DOCKER_IMAGE}:${ONEC_VERSION}

#COPY --from=base /opt /opt 

ADD https://github.com/just-containers/s6-overlay/releases/download/v1.21.8.0/s6-overlay-amd64.tar.gz /tmp/

ENV LANG ru_RU.UTF-8
ENV OSCRIPTBIN=/usr/local/bin/ovm/stable/bin
ENV PATH="$OSCRIPTBIN:$PATH"

#COPY ./configs/client-vnc/rootfs/ /

ENV DISPLAY=:0
ENV DISPLAY_WIDTH=1440
ENV DISPLAY_HEIGHT=900

EXPOSE 5900

ENTRYPOINT ["/init"]
