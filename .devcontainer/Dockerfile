FROM debian:10

LABEL org.opencontainers.image.source https://github.com/GetGatekeeper/gatekeeper-snap

RUN apt-get update && apt-get install -y \
       vim \
       zsh \
       iputils-ping \
       dnsutils \
       telnet \
       netcat \
       procps \
       lsof \
       apt-transport-https \
       ca-certificates \
       curl \
       gnupg \
       gnupg-agent \
       software-properties-common \
       htop \
    && curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - \
    && if [ "$(uname -m)" = 'x86_64' ]; then \
        add-apt-repository \
        "deb [arch=amd64] https://download.docker.com/linux/debian \
        $(lsb_release -cs) \
        stable"; \
       else \
        add-apt-repository \
        "deb [arch=arm64] https://download.docker.com/linux/debian \
        $(lsb_release -cs) \
        stable"; \
       fi \
    && apt-get update \
    && apt-get install -y docker-ce docker-ce-cli containerd.io \
    && ln -s /var/run/docker-host.sock /var/run/docker.sock  \
    && sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended \
    && rm -rf /var/lib/apt/lists/*