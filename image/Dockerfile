ARG BASE_IMAGE=ubuntu:18.04
FROM $BASE_IMAGE
MAINTAINER Phusion <info@phusion.nl>

ARG QEMU_ARCH
ADD x86_64_qemu-${QEMU_ARCH}-static.tar.gz /usr/bin

COPY . /bd_build

ENV DISABLE_SYSLOG=1
ENV DISABLE_SSH=1
ENV DISABLE_CRON=1

RUN /bd_build/prepare.sh && \
	/bd_build/system_services.sh && \
	/bd_build/utilities.sh && \
	/bd_build/cleanup.sh

ENV DEBIAN_FRONTEND="teletype" \
    LANG="en_US.UTF-8" \
    LANGUAGE="en_US:en" \
    LC_ALL="en_US.UTF-8"

CMD ["/sbin/my_init"]
