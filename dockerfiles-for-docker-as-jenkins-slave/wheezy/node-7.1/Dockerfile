FROM node:7.1.0-wheezy
RUN printf 'APT::Install-Recommends "0";\nAPT::Install-Suggests "0";\n' > /etc/apt/apt.conf.d/no-recommands
RUN echo "deb-src http://httpredir.debian.org/debian wheezy main" >> /etc/apt/sources.list && \
    echo "deb-src http://httpredir.debian.org/debian wheezy-updates main" >> /etc/apt/sources.list && \
    echo "deb-src http://security.debian.org wheezy/updates main" >> /etc/apt/sources.list

RUN apt-get -qqy update && apt-get -y install \
    apt-transport-https ca-certificates curl \
    openjdk-7-jre-headless sudo ssh locales \
    build-essential git libevent-dev \
    libssl-dev libxslt1-dev lsb-release pdftk pkg-config rsync \
    wget zlib1g-dev

# Locales
RUN echo "LANG=en_US.UTF-8" > /etc/default/locale && \
    echo "LANGUAGE=en_US:en" >> /etc/default/locale && \
    echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen && \
    update-locale

# Jenkins user
RUN useradd -m -s /bin/bash jenkins && \
    echo jenkins:jenkins | chpasswd && \
    echo "jenkins ALL=(root) NOPASSWD: ALL" > /etc/sudoers.d/jenkins && \
    chmod 440 /etc/sudoers.d/jenkins && \
    mkdir -p /var/run/sshd

EXPOSE 22
VOLUME /var/lib/docker
CMD ["/usr/sbin/sshd", "-D"]