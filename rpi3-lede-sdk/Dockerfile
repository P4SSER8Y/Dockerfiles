FROM p4sser8y/ubuntu-ustc:xenial

MAINTAINER p4sser8y <P4SSER8Y@outlook.com>

RUN apt-get update \
    && apt-get install -y -q --no-install-recommends wget xz-utils automake autoconf autopoint make cmake

WORKDIR /tmp
RUN wget --progress=dot:giga --no-check-certificate -O lede-sdk.tar.xz "https://downloads.openwrt.org/releases/17.01.4/targets/brcm2708/bcm2710/lede-sdk-17.01.4-brcm2708-bcm2710_gcc-5.4.0_musl-1.1.16_eabi.Linux-x86_64.tar.xz"
RUN tar xf lede-sdk.tar.xz \
    && rm -f lede-sdk.tar.xz \
    && mv /tmp/lede-sdk-17.01.4-brcm2708-bcm2710_gcc-5.4.0_musl-1.1.16_eabi.Linux-x86_64 /root/lede-sdk

ENV PATH="/root/lede-sdk/staging_dir/toolchain-arm_cortex-a53+neon-vfpv4_gcc-5.4.0_musl-1.1.16_eabi/bin:${PATH}"
ENV HOST="arm-openwrt-linux-muslgnueabi"

WORKDIR /root

ENTRYPOINT echo \$HOST=$HOST && /bin/bash

