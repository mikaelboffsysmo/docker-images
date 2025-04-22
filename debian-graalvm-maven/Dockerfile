FROM debian:10

# Metadados da imagem
LABEL maintainer="mikaelboffsysmo" \
      description="Imagem baseada em Debian 10, com GraalVM Mandrel Java 17 23.0.6.0-Final e Maven 3.6.3" \
      version="1.0"

# Variáveis
ENV MANDREL_VERSION=23.0.6.0-Final
ENV MANDREL_DIR=mandrel-java17-${MANDREL_VERSION}
ENV MANDREL_URL=https://github.com/graalvm/mandrel/releases/download/mandrel-${MANDREL_VERSION}/${MANDREL_DIR}-linux-amd64-${MANDREL_VERSION}.tar.gz
ENV MAVEN_VERSION=3.6.3
ENV MAVEN_DIR=apache-maven-${MAVEN_VERSION}

# Dependências
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        git wget curl gcc libfreetype6-dev build-essential libz-dev zlib1g-dev ca-certificates docker.io && \
    update-ca-certificates -f

# Mandrel
RUN wget -O /tmp/graalvm.tar.gz ${MANDREL_URL} && \
    tar -xzf /tmp/graalvm.tar.gz -C /opt && \
    rm /tmp/graalvm.tar.gz

ENV GRAALVM_HOME=/opt/${MANDREL_DIR}
ENV JAVA_HOME=$GRAALVM_HOME
ENV PATH=$GRAALVM_HOME/bin:$PATH

# Maven
RUN wget -O /tmp/maven.tar.gz https://archive.apache.org/dist/maven/maven-3/${MAVEN_VERSION}/binaries/${MAVEN_DIR}-bin.tar.gz && \
    tar -xzvf /tmp/maven.tar.gz -C /opt && \
    rm /tmp/maven.tar.gz

ENV MAVEN_HOME=/opt/${MAVEN_DIR}
ENV PATH=$MAVEN_HOME/bin:$PATH

RUN java -version && mvn -version && docker --version
