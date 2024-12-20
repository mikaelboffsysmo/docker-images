# Extende da imagem base cypress/browsers:node-22.12.0-chrome-131.0.6778.139-1-ff-133.0.3-edge-131.0.2903.99-1
FROM cypress/browsers:node-22.12.0-chrome-131.0.6778.139-1-ff-133.0.3-edge-131.0.2903.99-1

# Metadados da imagem
LABEL maintainer="mikaelboffsysmo" \
      description="Imagem baseada em cypress/browsers:node-22.12.0-chrome-131.0.6778.139-1-ff-133.0.3-edge-131.0.2903.99-1 com Google Cloud CLI instalado." \
      version="1.1"

# Instalação de pacotes necessários e configuração do Google Cloud CLI
RUN cp /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime && \
    echo "America/Sao_Paulo" > /etc/timezone && \
    wget -q https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-473.0.0-linux-x86_64.tar.gz -O - | tar -zx && \
    # Instalar o Google Cloud CLI
    ./google-cloud-sdk/install.sh -q --usage-reporting=false --additional-components beta && \
    # Disponibilizar o binário no PATH
    echo "export PATH=/google-cloud-sdk/bin:\$PATH" >> /etc/profile.d/google-cloud-sdk.sh && \
    chmod +x /etc/profile.d/google-cloud-sdk.sh

# Define o diretório de trabalho padrão
WORKDIR /app

# Exporta o PATH para todos os containers que usarem essa imagem
ENV PATH="/google-cloud-sdk/bin:$PATH"

# Comando padrão
CMD ["node"]
