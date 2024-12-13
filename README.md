# Repositório de Build e Deploy de Imagens Docker

Este repositório é usado para criar e publicar duas imagens Docker no Docker Hub:

- **`node-alpine-git`**: Baseada em `node:18-alpine` com Git instalado.
- **`node-alpine-deploy`**: Baseada em `node:18-alpine` com Git, Python3, Pip, Wget e Bash instalados.

## Configuração

1. Crie as variáveis secretas no GitHub:
   - `DOCKER_USERNAME`: Seu nome de usuário no Docker Hub.
   - `DOCKER_PASSWORD`: Sua senha ou token de acesso ao Docker Hub.

2. Use o GitHub Actions para realizar o build e deploy das imagens.

## Executar a Pipeline

Você pode disparar o workflow manualmente em **Actions > Docker Build and Push**, especificando:

- `image_name`: O nome da imagem (`node-alpine-git` ou `node-alpine-deploy`).
- `tag`: A tag da imagem (por exemplo, `v1.0.0`, `latest`).

## Estrutura do Repositório

- `node-alpine-git/`: Dockerfile para a imagem `node-alpine-git`.
- `node-alpine-deploy/`: Dockerfile para a imagem `node-alpine-deploy`.
