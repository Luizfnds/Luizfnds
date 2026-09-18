# Luiz Eduardo

Back-end .NET. Construo APIs e microsserviços event-driven — mensageria, autenticação
e observabilidade — e cuido do deploy em containers e cloud. Também desenvolvo mobile
em Flutter.

### Stack

- **Back-end** — `C#` `.NET 8` `Clean Architecture` `DDD` `CQRS` `MediatR` `FluentValidation` `RabbitMQ` `JWT`
- **Dados** — `SQL Server` `EF Core` `SQLite` `MongoDB` `Redis` `Elasticsearch`
- **Infra & Cloud** — `Docker` `Kubernetes (EKS)` `AWS Lambda` `Cognito` `GitHub Actions` `Prometheus` `Grafana`
- **Mobile** — `Flutter`

### Demonstrações técnicas

Os dois primeiros projetos são o mesmo produto em momentos diferentes: um MVP monolítico
e sua quebra em microsserviços. O terceiro é um sistema independente, construído do zero
já com arquitetura distribuída.

**1. [fiap-cloud-games](https://github.com/Luizfnds/fiap-cloud-games)** — *o ponto de partida*

Plataforma de venda de jogos digitais (catálogo, promoções, biblioteca pessoal) como uma
API REST monolítica em .NET 8. O foco aqui foi a **base arquitetural**: Clean Architecture
com DDD isolando as regras de negócio no domínio, CQRS com MediatR separando leitura de
escrita, validação declarativa com FluentValidation e autenticação JWT via AWS Cognito com
dois níveis de acesso. Um monolito bem modularizado — que é o que torna o passo seguinte
possível.

**2. [TC-FIAP-Grupo-11](https://github.com/TC-FIAP-Grupo-11)** — *a evolução para distribuído*

O mesmo produto decomposto em **4 microsserviços** (NOMES DOS 4 SERVIÇOS), cada um com seu
próprio banco e ciclo de vida. O que a decomposição trouxe:

- **Comunicação assíncrona** — os serviços conversam por eventos no RabbitMQ
  (`UserCreatedEvent`, `OrderPlacedEvent`), sem acoplamento direto
- **Contratos compartilhados** — biblioteca publicada como pacote NuGet com os
  contratos de eventos e o setup do MassTransit, eliminando duplicação entre os serviços
- **Serverless** — processamento de pagamentos e NOME DA OUTRA FUNÇÃO extraídos para
  AWS Lambda, invocadas pelas APIs via SDK
- **Persistência poliglota** — cada necessidade com a ferramenta certa: SQL Server para o
  transacional, Redis (cache-aside) para listagens, Elasticsearch para busca fuzzy e
  MongoDB para avaliações de jogos
- **Deploy e operação** — Docker Compose para desenvolvimento, Kubernetes no EKS atrás de
  API Gateway em produção, com CI/CD no GitHub Actions, scan de vulnerabilidades com
  Trivy e push para NOME DO REGISTRY

**3. [conexao-solidaria](https://github.com/Luizfnds/conexao-solidaria)** — *distribuído desde o primeiro commit*

Plataforma de gestão de campanhas de doação para ONGs, construída sozinho do zero. O
desafio central foi **não perder doação**: o endpoint valida, publica o evento no RabbitMQ
e responde `202 Accepted` na hora; um worker separado consome a fila e consolida o valor
arrecadado — o pico de requisições não derruba o processamento, e falhas no consumo não
devolvem erro ao doador. Além disso: JWT com RBAC (GestorONG e Doador), Clean Architecture
com as regras de negócio no domínio, e deploy em Kubernetes com observabilidade de verdade:
health checks, métricas no Prometheus e dashboard Grafana provisionado por código.

---

📫 [linkedin.com/in/luizfnds](https://linkedin.com/in/luizfnds)
