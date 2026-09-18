Back-end .NET. Construo APIs e microsserviços event-driven — mensageria, autenticação
e observabilidade — e cuido do deploy em containers e cloud. Também desenvolvo mobile
em Flutter.

## Stack

- **Back-end** — `C#` `.NET 8` `Clean Architecture` `DDD` `CQRS` `MediatR` `FluentValidation` `RabbitMQ` `JWT`
- **Dados** — `SQL Server` `EF Core` `SQLite` `MongoDB` `Redis` `Elasticsearch`
- **Infra & Cloud** — `Docker` `Kubernetes (EKS)` `AWS Lambda` `Cognito` `GitHub Actions` `Prometheus` `Grafana`
- **Mobile** — `Flutter`

## FIAP Cloud Games

Plataforma de venda de jogos digitais e projeto central da pós em Arquitetura de Sistemas
.NET, evoluída ao longo de quatro fases — do MVP à operação cloud-native. Um repositório
para cada lado dessa virada:

**[fiap-cloud-games](https://github.com/Luizfnds/fiap-cloud-games)** — *o MVP*<br>
Monolito por decisão de projeto, para validar o produto rápido. API REST em .NET 8 com
usuários, catálogo, promoções e biblioteca, JWT via AWS Cognito. Clean Architecture com
DDD, CQRS e EF Core — modular o bastante para ser quebrado depois sem reescrever o domínio.

**[TC-FIAP-Grupo-11](https://github.com/TC-FIAP-Grupo-11)** — *a evolução*<br>
O monolito virou gargalo e foi decomposto em quatro microsserviços autônomos, um repositório
cada, comunicando por eventos no RabbitMQ. Pagamento e notificação em AWS Lambda atrás de
API Gateway, deploy em EKS, CI/CD no GitHub Actions e persistência poliglota — Redis para
cache, Elasticsearch para busca e MongoDB para avaliações.

## Conexão Solidária

**[conexao-solidaria](https://github.com/Luizfnds/conexao-solidaria)** — *hackathon final*<br>
Plataforma de campanhas de doação para uma ONG, feita do zero e sozinho. A API não grava a
doação no banco: valida, publica o evento no RabbitMQ e responde `202 Accepted`, enquanto um
Worker consome a fila e consolida o valor — pico de tráfego não derruba o processamento e
nenhuma doação se perde. JWT com RBAC, Kubernetes com health checks e Prometheus + Grafana
provisionados por código.

---

📫 [linkedin.com/in/luizfnds](https://linkedin.com/in/luizfnds)
