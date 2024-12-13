# Extende da imagem base node:18-alpine
FROM node:18-alpine

# Metadados da imagem
LABEL maintainer="mikaelboffsysmo" \
      description="Imagem baseada em node:18-alpine com Git instalado." \
      version="1.0"

# Instalação do Git
RUN apk add --no-cache git

# Define o diretório de trabalho padrão
WORKDIR /app

# Comando padrão
CMD ["node"]
