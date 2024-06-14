# Projeto de Demonstração de CI/CD para Go

Este projeto de exemplo demonstra a implementação de um pipeline de Integração Contínua e Entrega Contínua (CI/CD) para aplicações Go, utilizando o GitHub Actions como plataforma de automação.

## A Missão

**Criar um render e fazer o deploy via actions para um webservice gratuito!**

Este projeto tem como objetivo principal demonstrar como construir e implantar automaticamente um serviço web Go simples em um ambiente de produção, utilizando o Render.com como provedor de hospedagem gratuito e o GitHub Actions para automatizar o processo de CI/CD.

## Estrutura do Projeto

```
├── Dockerfile          # Define a imagem Docker para o aplicativo
├── go.mod              # Gerencia as dependências do projeto Go
├── main.go            # Código fonte principal do aplicativo (Hello World)
├── main_test.go       # Testes unitários para o aplicativo
└── .github
    ├── dependabot.yml   # Configuração do Dependabot para atualização automática de dependências
    └── workflows
        └── ci.yml        # Workflow do GitHub Actions para o pipeline de CI/CD
```

## Pipeline de CI/CD

O pipeline de CI/CD é definido no arquivo `.github/workflows/ci.yml` e executa as seguintes etapas:

1. **Build:** Compila o código Go para gerar o executável.
2. **Lint:** Analisa o código Go em busca de problemas de estilo e erros potenciais usando o `golangci-lint`.
3. **Test:** Executa os testes unitários do projeto.
4. **Security:** Verifica vulnerabilidades no código e nas dependências usando o Trivy.
5. **Deploy:**
   - Cria uma imagem Docker do aplicativo.
   - Faz o login no Docker Hub.
   - Envia a imagem para o Docker Hub.
   - Implanta o aplicativo no Render.com usando a imagem do Docker Hub.

## Dependabot

O Dependabot é configurado para verificar e atualizar automaticamente as dependências do projeto Go, conforme definido no arquivo `.github/dependabot.yml`.

## Como usar

1. Clone este repositório.
2. Crie um serviço no Render.com compatível com seu projeto Go.
3. Configure as seguintes secrets no seu repositório GitHub:
   - `DOCKER_USERNAME`: Seu nome de usuário no Docker Hub.
   - `DOCKER_PASSWORD`: Sua senha do Docker Hub.
   - `RENDER_SERVICE_ID`: O ID do serviço no Render.com.
   - `RENDER_API_KEY`: Sua chave de API do Render.com.
4. Faça um push para o seu repositório GitHub para iniciar o pipeline de CI/CD.

## Observações

* Este é um projeto de exemplo simplificado. Em um projeto real, você provavelmente teria mais etapas no pipeline, como testes de integração, análise de cobertura de código, etc.
* Adapte as configurações do Dockerfile e do Render.com para as suas necessidades específicas.

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests.
