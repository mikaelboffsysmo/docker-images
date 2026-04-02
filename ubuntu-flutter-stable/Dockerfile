# Usar Ubuntu 22.04 como base
FROM ubuntu:22.04

# Metadados da imagem
LABEL maintainer="mikaelboffsysmo" \
      description="Imagem baseada em Ubuntu com flutter e android para build de aplicação android." \
      version="1.0"

# Evitar diálogos interativos durante a instalação
ENV DEBIAN_FRONTEND=noninteractive

# Instalar dependências básicas, locales e software-properties-common
RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    xz-utils \
    zip \
    libglu1-mesa \
    openjdk-21-jdk \
    ruby-full \
    build-essential \
    libsqlite3-dev \
    locales \
    software-properties-common \
    && rm -rf /var/lib/apt/lists/*

# Configurar Locale para UTF-8 pt_BR (Exigência do Fastlane)
RUN locale-gen pt_BR.UTF-8
ENV LANG pt_BR.UTF-8
ENV LANGUAGE pt_BR:pt
ENV LC_ALL pt_BR.UTF-8

# Instalar GitLab CLI (glab)
RUN curl -L https://gitlab.com/gitlab-org/cli/-/releases/v1.91.0/downloads/glab_1.91.0_linux_amd64.deb -o glab.deb && \
    dpkg -i glab.deb && \
    rm glab.deb

# Instalar Fastlane e Bundler
RUN gem install fastlane bundler -NV

# Configurar variáveis de ambiente para Android e Java
ENV JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64
ENV ANDROID_SDK_ROOT=/opt/android-sdk
ENV ANDROID_HOME=$ANDROID_SDK_ROOT
ENV PATH=$PATH:$ANDROID_SDK_ROOT/cmdline-tools/latest/bin:$ANDROID_SDK_ROOT/platform-tools:$ANDROID_SDK_ROOT/emulator

# Instalar Android SDK Command-line tools
RUN mkdir -p $ANDROID_SDK_ROOT/cmdline-tools && \
    curl -o cmdline-tools.zip https://dl.google.com/android/repository/commandlinetools-linux-11076708_latest.zip && \
    unzip cmdline-tools.zip -d $ANDROID_SDK_ROOT/cmdline-tools && \
    mv $ANDROID_SDK_ROOT/cmdline-tools/cmdline-tools $ANDROID_SDK_ROOT/cmdline-tools/latest && \
    rm cmdline-tools.zip

# Aceitar licenças e instalar Platform Tools e Build Tools (Versões detectadas no log como necessárias)
RUN yes | sdkmanager --licenses && \
    sdkmanager "platform-tools" \
    "platforms;android-34" "platforms;android-35" "platforms;android-36" \
    "build-tools;34.0.0" "build-tools;35.0.0" \
    "ndk;27.2.12479018" "ndk;28.2.13676358" "cmake;3.22.1"

# Instalar Flutter (Estável)
ENV FLUTTER_HOME=/opt/flutter
ENV PATH=$PATH:$FLUTTER_HOME/bin

RUN git clone https://github.com/flutter/flutter.git -b stable $FLUTTER_HOME && \
    flutter --version

# Pré-download de artefatos para Android
RUN flutter precache --android

# Verificar instalação
RUN flutter doctor

WORKDIR /app
