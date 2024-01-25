ARG ARCH
FROM ${ARCH}/debian:bookworm-slim

RUN apt-get update -qq \
 && apt-get upgrade -y \
 && apt-get dist-upgrade -y -q \
# Install build dependencies
 && apt-get install -y -q \
        ccache \
	cmake \
        git-core \
        make \
        python3-dev \
        python3-jinja2 \
        python3-minimal \
        python3-nose \
        python3-pip \
        python3-pycparser \
        python3-rednose \
        python3-yaml \
 	gcc \
	clang \
	clang-tidy \
	valgrind \
 && apt-get autoremove -y \
# Python deps
 && pip3 install --break-system-packages PyYAML pytest pytest-xdist pycparser py-cpuinfo \
# AStyle
 && git clone --depth=1 --branch=3.4.11 https://gitlab.com/saalen/astyle.git /tmp/astyle \
 && cd /tmp/astyle \
 && mkdir build \
 && cd build \
 && cmake -DCMAKE_BUILD_TYPE=Release .. \
 && make -j3 \
 && make install \
 && rm -rf /tmp/astyle \
# Cleanup
 && rm -rf /var/lib/apt/lists/* /var/cache/apt/*

