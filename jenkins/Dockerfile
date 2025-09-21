FROM jenkins/jenkins:lts

USER root

RUN apt-get update && apt-get install -y \
    wget \
    curl \
    unzip \
    gnupg \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /opt/jdk21 && \
    curl -L --fail -o /tmp/openjdk21.tar.gz \
      "https://api.adoptium.net/v3/binary/latest/21/ga/linux/x64/jdk/hotspot/normal/eclipse" && \
    tar -xvzf /tmp/openjdk21.tar.gz -C /opt/jdk21 --strip-components=1 && \
    rm /tmp/openjdk21.tar.gz


ENV JAVA_HOME=/opt/jdk21
ENV PATH="${JAVA_HOME}/bin:${PATH}"

RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && \
    apt-get install -y nodejs && \
    npm install -g npm@latest

USER jenkins
