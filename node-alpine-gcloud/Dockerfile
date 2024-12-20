# Extende da imagem base node:18-alpine
FROM node:18-alpine

# Metadados da imagem
LABEL maintainer="mikaelboffsysmo" \
      description="Imagem baseada em node:18-alpine com Git, Python3, Pip, Wget, Bash e Google Cloud CLI instalados." \
      version="1.1"

# Instalação de pacotes necessários e configuração do Google Cloud CLI
RUN apk add --no-cache \
    git \
    python3 \
    py3-pip \
    wget \
    bash && \
    # Baixar o Google Cloud CLI
    wget -q https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-473.0.0-linux-x86_64.tar.gz -O - | tar -zx && \
    # Instalar o Google Cloud CLI
    ./google-cloud-sdk/install.sh -q --usage-reporting=false --additional-components beta && \
    # Disponibilizar o binário no PATH
    echo "export PATH=/google-cloud-sdk/bin:\$PATH" >> /etc/profile.d/google-cloud-sdk.sh && \
    chmod +x /etc/profile.d/google-cloud-sdk.sh && \
    # Limpeza de arquivos temporários para reduzir o tamanho da imagem
    rm -rf /var/cache/apk/*

# Define o diretório de trabalho padrão
WORKDIR /app

# Exporta o PATH para todos os containers que usarem essa imagem
ENV PATH="/google-cloud-sdk/bin:$PATH"

# Comando padrão
CMD ["node"]
