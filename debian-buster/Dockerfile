ARG ARCH
FROM multiarch/debian-debootstrap:${ARCH}-buster

RUN apt-get update -qq \
 && apt-get upgrade -y \
 && apt-get dist-upgrade -y -q \
# Install build dependencies
 && apt-get install -y -q \
        astyle \
        clang \
        clang-tidy \
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
 # Install GCC 9
 && echo "deb http://deb.debian.org/debian experimental main" >> /etc/apt/sources.list \
 && apt-get update -qq \
 && apt-get -t experimental install -y -q gcc clang \
 && apt-get autoremove -y \
# Cleanup
 && rm -rf /var/lib/apt/lists/* /var/cache/apt/*
