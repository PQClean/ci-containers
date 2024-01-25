FROM pqclean/multiarch-debian-debootstrap:powerpc-sid

COPY ppc-sources.list /etc/apt/sources.list

ENV PQCLEAN_SKIP_TESTS=clang_tidy,functest_sanitizers,astyle

RUN  \
 PKGVER=$(wget -O- http://ftp.ports.debian.org/debian-ports/pool/main/d/debian-ports-archive-keyring/ 2>/dev/null | sed -n 's/.*-keyring_\(.*\)_all.*/\1/p' -) \
 && echo "Fetching debian keyring version ${PKGVER}" \
 && wget http://ftp.ports.debian.org/debian-ports/pool/main/d/debian-ports-archive-keyring/debian-ports-archive-keyring_${PKGVER}_all.deb \
# Install debian-ports keychain
 && dpkg -i debian-ports-archive-keyring_${PKGVER}_all.deb \
 && rm debian-ports-archive-keyring_${PKGVER}_all.deb \
# Update to unstable
 && apt-get update -qq \
 && apt-get upgrade -q -y \
 && apt-get dist-upgrade -q -y \
# Install build dependencies
 && apt-get install -q -y \
        ccache \
        clang-15 \
        clang-tidy-15 \
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
 && apt-get autoremove -y \
 && update-alternatives --install /usr/bin/clang clang /usr/bin/clang-15 100 \
# Python deps
 && pip3 install --break-system-packages PyYAML pytest pytest-xdist pycparser py-cpuinfo \
# Cleanup
 && rm -rf /var/lib/apt/lists/* /var/cache/apt/*
