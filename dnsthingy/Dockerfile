FROM debian:10.5

ENV DEBIAN_FRONTEND noninteractive

ARG DT_VERSION=3.4.10
ARG DT_BUILD=1

RUN apt-get update && \
    apt-get install -y \
    libssl-dev \
    curl

RUN mkdir -p /opt/bin \
    && curl https://dl.adamnet.works/firmware/debian/debian10-test-${DT_VERSION}-${DT_BUILD}.tar.gz -o /opt/bin/adamone.tar.gz \
    && tar -xzf /opt/bin/adamone.tar.gz -C /opt/bin \
    && rm /opt/bin/adamone.tar.gz

ADD dnsthingy/entry-point.sh /opt/bin/

# DNS
EXPOSE 53/udp
EXPOSE 53/tcp

# Web
EXPOSE 80

CMD [ "/opt/bin/entry-point.sh" ]
