# Extende da imagem base node:18-alpine
FROM node:18-alpine

# Metadados da imagem
LABEL maintainer="mikaelboffsysmo" \
      description="Imagem baseada em node:18-alpine com Git, Python3, Pip, Wget e Bash instalados." \
      version="1.0"

# Instalação de pacotes necessários
RUN apk add --no-cache \
    git \
    python3 \
    py3-pip \
    wget \
    bash

# Define o diretório de trabalho padrão
WORKDIR /app

# Comando padrão
CMD ["node"]
