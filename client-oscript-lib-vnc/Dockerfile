ARG DOCKER_REGISTRY_URL
ARG DOCKER_IMAGE
ARG ONEC_VERSION


FROM ${DOCKER_REGISTRY_URL}/${DOCKER_IMAGE}:${ONEC_VERSION}
ARG ssh_prv_key
ARG ssh_pub_key

# Авторизация SSH Host
RUN mkdir -p /root/.ssh \
    && chmod 0700 /root/.ssh \
    && ssh-keyscan -t rsa coderepo.corp.tander.ru >> /root/.ssh/known_hosts \
    && ssh-keyscan -t rsa 10.8.98.66 >> /root/.ssh/known_hosts

# загрузка библиотеки
RUN echo "$ssh_prv_key" > /root/.ssh/id_rsa \
    && echo "$ssh_pub_key" > /root/.ssh/id_rsa.pub \
    && chmod 600 /root/.ssh/id_rsa \
    && chmod 600 /root/.ssh/id_rsa.pub \
    && git clone git@coderepo.corp.tander.ru:1c/onescript.git /tmp/onescript \
    && rm -r /usr/local/bin/ovm/stable/lib/* \
    && cp -r /tmp/onescript/lib/* /usr/local/bin/ovm/stable/lib \
    && rm -r /tmp/onescript \
    && rm -r /root/.ssh

ENV DISPLAY=:0
ENV DISPLAY_WIDTH=1440
ENV DISPLAY_HEIGHT=900

EXPOSE 5900

ENTRYPOINT ["/init"]