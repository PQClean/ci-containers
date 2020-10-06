FROM pqclean/multiarch-debian-debootstrap:powerpc-sid

COPY ppc-sources.list /etc/apt/sources.list

RUN wget http://ftp.ports.debian.org/debian-ports/pool/main/d/debian-ports-archive-keyring/debian-ports-archive-keyring_2019.11.05_all.deb \
# Install debian-ports keychain
 && dpkg -i debian-ports-archive-keyring_2019.11.05_all.deb \
 && rm debian-ports-archive-keyring_2019.11.05_all.deb \
# Update to unstable
 && apt-get update -qq \
 && apt-get upgrade -q -y \
 && apt-get dist-upgrade -q -y \
# Install build dependencies
 && apt-get install -q -y \
        astyle \
        ccache \
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
# Python deps
 && pip3 install PyYAML pytest pytest-xdist pycparser py-cpuinfo \
# Cleanup
 && rm -rf /var/lib/apt/lists/* /var/cache/apt/*
