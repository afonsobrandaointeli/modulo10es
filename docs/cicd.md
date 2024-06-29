## Roadmap das Aulas

Confira o cronograma das aulas e os tópicos que serão abordados:

![Roadmap das Aulas](https://res.cloudinary.com/dyhjjms8y/image/upload/v1717115396/Captura_de_tela_2024-05-31_002953_evnk75.png)

---

## Esteira de CI como guardiã da qualidade

| Curso                                                                                                                   | Semana   | Pontuação |
| ----------------------------------------------------------------------------------------------------------------------- | -------- | --------- |
| [Introdução ao fornecimento de serviços de qualidade com DevOps](https://learn.microsoft.com/pt-br/devops/deliver/delivering-quality-services-with-devops) | Semana 08 | 0         |
| [Caso de uso: Como a Microsoft fornece software com o DevOps](https://learn.microsoft.com/pt-br/devops/deliver/how-microsoft-delivers-devops) | Semana 08 | 0         |
| [SRE e Disponibilidade: Experiências e desafios do DevOps no Mercado Livre](https://www.youtube.com/watch?v=_XIIG4Ga3L8) | Semana 08 | 0         |
| [Plataforma Fury no Mercado Livre](https://www.youtube.com/watch?v=jhSoFPONQ5s) | Semana 08 | 0         |
| [Garantia da qualidade de software](https://integrada.minhabiblioteca.com.br/reader/books/9788580555349/cfi/475!/4/2@100:0.00) | Semana 08 | 0         |

---

## Esquenta Kahoot!

Prepare-se para o quiz! Teste seus conhecimentos sobre DevOps e os temas abordados nos autoestudos. Clique no botão abaixo para acessar o Kahoot! e entrar no jogo.

<a href="https://kahoot.it/" target="_blank" class="btn btn-lg btn-warning">
  <i class="fas fa-play me-2"></i> Jogar Kahoot!
</a>

---

## O que é CI/CD?

CI/CD, ou Integração Contínua e Entrega/Implantação Contínua, é um conjunto de práticas que automatizam o processo de desenvolvimento, teste e implantação de software. O objetivo é entregar software de forma mais rápida, frequente e confiável.

#### Integração Contínua (CI)

A CI envolve a integração frequente do código de todos os desenvolvedores em um repositório central. Cada integração passa por testes automatizados para garantir que o código não introduza novos erros.

- Integração frequente de código
- Testes automatizados
- Feedback rápido sobre erros

#### Entrega/Implantação Contínua (CD)

A CD automatiza o processo de implantação do software em diferentes ambientes, como desenvolvimento, teste e produção. O objetivo é garantir que o software esteja sempre pronto para ser implantado em produção.

- Implantação automatizada
- Ambientes de teste realistas
- Entrega rápida de novas funcionalidades

O CI/CD é essencial para equipes que desejam entregar software de alta qualidade de forma rápida e eficiente. Ele ajuda a reduzir o tempo de lançamento, aumentar a frequência de entregas e melhorar a qualidade do software.

![Diagrama CI/CD](https://res.cloudinary.com/dyhjjms8y/image/upload/v1717111988/Captura_de_tela_2024-05-30_233310_enkayb.png)

---

## Garantia da Qualidade de Software

A garantia da qualidade de software (SQA) é um conjunto de atividades sistemáticas que visam garantir que o software atenda aos requisitos e expectativas dos usuários. Isso envolve a aplicação de boas práticas em todas as etapas do desenvolvimento, desde o planejamento até a implantação e manutenção.

#### Boas Práticas de SQA

- **Testes automatizados:** Testes unitários, de integração e de sistema automatizados para garantir a funcionalidade e o desempenho do software.
- **Análise estática de código:** Ferramentas como linters e analisadores estáticos para identificar problemas de código, como erros de sintaxe, vulnerabilidades de segurança e problemas de estilo.
- **Revisão de código:** Revisão manual do código por outros desenvolvedores para identificar problemas e garantir a qualidade do código.
- **Monitoramento contínuo:** Monitoramento do software em produção para identificar problemas de desempenho, erros e falhas de segurança.
- **Integração contínua e entrega contínua (CI/CD):** Automação do processo de build, teste e implantação para garantir que o software seja entregue de forma rápida e confiável.

---

## Act: Simulando GitHub Actions Localmente

O Act é uma ferramenta poderosa que permite simular localmente os fluxos de trabalho do GitHub Actions. Isso agiliza o desenvolvimento e a depuração de seus pipelines de CI/CD, permitindo que você teste suas ações antes de enviá-las para o GitHub.

<a href="https://github.com/nektos/act" target="_blank" class="btn btn-primary btn-lg">
  <i class="fab fa-github me-2"></i> Repositório do Act no GitHub
</a>

#### Dica

Quer aprender mais sobre como usar o Act? Confira este artigo: [Test your GitHub Actions locally with Act](https://medium.com/it-dead-inside/test-your-github-actions-locally-with-act-c3790834fc3a)

#### Instalação no Windows

Para instalar o Act no Windows, você pode seguir os seguintes passos:

1. **Instale o Chocolatey:** O Chocolatey é um gerenciador de pacotes para Windows que facilita a instalação de softwares. Você pode instalá-lo seguindo as instruções no site oficial: [https://chocolatey.org/install](https://chocolatey.org/install)
2. **Instale o Act:** Após instalar o Chocolatey, abra um terminal com privilégios de administrador e execute o seguinte comando:
   ```sh
   choco install act-cli
   ```
3. **Verifique a instalação:** Após a instalação, você pode verificar se o Act está funcionando corretamente executando o comando:
   ```sh
   act --version
   ```

---

## Multi-Stage Builds: Eficiência e Segurança

Multi-stage builds são uma poderosa técnica do Docker que permite criar imagens menores e mais seguras, otimizando o processo de construção e reduzindo a superfície de ataque.

#### Dockerfile Original

```dockerfile
# Dockerfile
FROM golang:alpine

WORKDIR /app

COPY main.go main_test.go ./

RUN go mod init myapp
RUN go mod tidy
RUN go build -o main main.go

EXPOSE 8080

CMD ["go", "run", "main.go"]
```

#### Dockerfile Multi-Stage Otimizado

```dockerfile
# Estágio de construção
FROM golang:1.22 AS builder

WORKDIR /app
COPY . .

RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -o main .

# Estágio de produção
FROM alpine:latest
WORKDIR /app
COPY --from=builder /app/main .

EXPOSE 8080
CMD ["./main"]
```

---

## Desafio!

Em sala de aula, vamos abrir e revisar juntos o pipeline de CI/CD criado neste projeto. Seu desafio será:

1. Clonar o repositório.
2. Criar uma conta no Render.com.
3. Fazer o deploy da aplicação, personalizando-a para exibir seu nome em vez de "Hello World".
4. **Otimizar o Dockerfile utilizando a técnica de multi-stage build.**

[![Repositório do Projeto no GitHub](https://github.com/afonsobrandaointeli/cicd)](https://github.com/afonsobrandaointeli/cicd)

---

## Dicas para Limpar seu Docker

Mantenha seu ambiente Docker organizado e livre de recursos não utilizados com estes comandos úteis:

#### Comandos de Limpeza

```sh
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
docker rmi $(docker images -aq)
docker image prune -af
docker volume prune -f
docker network prune -f
docker system prune -af --volumes
```

**Atenção:** O comando `docker system prune -af --volumes` remove todos os containers parados, imagens não utilizadas, redes não referenciadas e volumes pendentes. Use com cuidado!

---

## Sua Opinião é Importante!

Deixe seu feedback com estrelas e comentários e ajude-nos a melhorar o Inteli e o curso de ES.
