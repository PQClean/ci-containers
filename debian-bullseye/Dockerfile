ARG ARCH
FROM multiarch/debian-debootstrap:${ARCH}-bullseye

RUN apt-get update -qq \
 && apt-get upgrade -y \
 && apt-get dist-upgrade -y -q \
# Install build dependencies
 && apt-get install -y -q \
        astyle \
        ccache \
        gcc \
        git-core \
        make \
        python3-dev \
        python3-minimal \
        python3-nose \
        python3-pip \
        python3-pycparser \
        python3-rednose \
        python3-yaml \
        valgrind \
# Install clang 9
 && echo "deb http://deb.debian.org/debian experimental main" >> /etc/apt/sources.list.d/experimental.list \
 && apt-get update -qq \
 && apt-get install -y -q clang-9 clang-tidy-9 \
 && update-alternatives --install /usr/bin/clang clang /usr/bin/clang-9 100 \
 && update-alternatives --install /usr/bin/clang-tidy clang-tidy /usr/bin/clang-tidy-9 100 \
 && apt-get autoremove -y \
# Python deps
 && pip3 install PyYAML pytest pytest-xdist pycparser py-cpuinfo \
# Cleanup
 && rm -rf /var/lib/apt/lists/* /var/cache/apt/*
