FROM alpine:3.19

ARG TIDEWAYS_ENVIRONMENT_DEFAULT=production
ARG DEBIAN_FRONTEND=noninteractive

ENV TIDEWAYS_ENVIRONMENT=$TIDEWAYS_ENVIRONMENT_DEFAULT

ENV TIDEWAYS_DAEMON_VERSION 1.8.40

RUN mkdir -p /var/run/tideways && \
    wget -qO tideways-daemon.tar.gz "https://s3-eu-west-1.amazonaws.com/tideways/daemon/${TIDEWAYS_DAEMON_VERSION}/tideways-daemon_linux_amd64-${TIDEWAYS_DAEMON_VERSION}.tar.gz" && \
    tar xzf tideways-daemon.tar.gz && \
    mv tideways-daemon_${TIDEWAYS_DAEMON_VERSION}/tideways-daemon /usr/bin/tideways-daemon && \
    chmod +x /usr/bin/tideways-daemon && \
    rm -rf tideways-daemon.tar.gz tideways-daemon_${TIDEWAYS_DAEMON_VERSION}

EXPOSE 9135

ENTRYPOINT ["tideways-daemon", "--hostname=tideways-daemon", "--address=0.0.0.0:9135"]
