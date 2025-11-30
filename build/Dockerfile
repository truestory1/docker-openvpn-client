FROM alpine:3.22.2

# renovate: datasource=repology depName=alpine_3_22/bash versioning=loose
ENV BASH_VERSION="5.2.37-r0"
# renovate: datasource=repology depName=alpine_3_22/bind-tools versioning=loose
ENV BIND_TOOLS_VERSION="9.20.16-r0"
# renovate: datasource=repology depName=alpine_3_22/iptables versioning=loose
ENV IPTABLES_VERSION="1.8.11-r1"
# renovate: datasource=repology depName=alpine_3_22/ip6tables versioning=loose
ENV IP6TABLES_VERSION="1.8.11-r1"
# renovate: datasource=repology depName=alpine_3_22/openvpn versioning=loose
ENV OPENVPN_VERSION="2.6.16-r0"

RUN set -ex \
    && apk update \
    && apk add --no-cache \
        bash${BASH_VERSION:+=$BASH_VERSION} \
        bind-tools${BIND_TOOLS_VERSION:+=$BIND_TOOLS_VERSION} \
        iptables${IPTABLES_VERSION:+=$IPTABLES_VERSION} \
        ip6tables${IP6TABLES_VERSION:+=$IP6TABLES_VERSION} \
        openvpn${OPENVPN_VERSION:+=$OPENVPN_VERSION} \
    && rm -rf /var/cache/apk/*  # Clean up cache to reduce layer size

COPY . /usr/local/bin

ENV KILL_SWITCH=on

ENTRYPOINT [ "entry.sh" ]
