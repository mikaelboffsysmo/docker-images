# Repositório de Build e Deploy de Imagens Docker

Este repositório é usado para criar e publicar imagens Docker no Docker Hub:

- **`node-alpine-gcloud`**: Baseada em `node:18-alpine` com Git, Python3, Pip, Wget e Bash instalados com o Gcloud instalado.

## Configuração

1. Crie as variáveis secretas no GitHub:
   - `DOCKER_USERNAME`: Seu nome de usuário no Docker Hub.
   - `DOCKER_PASSWORD`: Sua senha ou token de acesso ao Docker Hub.

2. Use o GitHub Actions para realizar o build e deploy das imagens.

## Executar a Pipeline

Você pode disparar o workflow manualmente em **Actions > Docker Build and Push**, especificando:

- `image_name`: O nome da imagem (`node-alpine-gcloud`).
- `tag`: A tag da imagem (por exemplo, `18`, `19`).

## Estrutura do Repositório

- `node-alpine-gcloud/`: Dockerfile para a imagem `node-alpine-gcloud`.