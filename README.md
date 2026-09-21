# Eduardo Henrique de Freitas Caro

Desenvolvedor Full Stack com foco em backend Java e infraestrutura na AWS, de Catanduva, SP.

Trabalho há mais de 3 anos com Java (Spring Boot), Node.js e React, e gosto de arquitetura backend, design de APIs e nuvem. Hoje sou Analista de Sistemas na Usina São Domingos, onde modernizei sistemas legados, automatizei infraestrutura na AWS e coloquei em produção pipelines de CI/CD. Também estou cursando a pós-graduação em Internet das Coisas no IFSP Catanduva.

## Projetos em destaque

### [Agendamento de Cargas API](https://github.com/eduardofcaro1/agendamento-cargas-api)

API REST em Java 21 e Spring Boot para agendar a chegada de veículos de carga em um pátio logístico. É a versão pública e genérica do sistema de agendamento que desenvolvi no trabalho.

O ponto central é a garantia de que dois veículos nunca ocupam o mesmo ponto ao mesmo tempo, mesmo com requisições simultâneas. Em vez de conferir conflitos no código, a regra fica no PostgreSQL, com uma *exclusion constraint*, e um teste dispara 10 requisições concorrentes para o mesmo horário e confirma que só uma é aceita.

O que tem de interessante:

- Conflito de horário garantido pelo banco, sem condição de corrida
- Autenticação stateless com Spring Security e JWT, senhas com BCrypt e perfis `ADMIN` e `OPERADOR`
- Eventos publicados em fila SQS com o padrão *transactional outbox*, sem perder mensagens entre o banco e a fila, e consumidor idempotente
- Regras de negócio puras, fora do Spring, e erros no formato RFC 7807
- Migrações com Flyway e testes de integração com PostgreSQL e ElasticMQ reais via Testcontainers
- Pipeline de CI no GitHub Actions

Tecnologias: Java 21, Spring Boot, Spring Security, JPA/Hibernate, PostgreSQL, Flyway, AWS SQS (ElasticMQ local), Testcontainers, Docker, GitHub Actions.

### [Serverless Ingest Pipeline](https://github.com/eduardofcaro1/serverless-ingest-pipeline)

API que recebe lotes de leituras de dispositivos, guarda o payload original no S3, normaliza os dados e grava tudo em PostgreSQL. Foi projetada para rodar em AWS Lambda dentro de uma VPC privada, com a infraestrutura definida em Terraform, e também roda localmente com Docker.

É a versão pública e genérica de um padrão que uso no trabalho: dados vindos de aplicações mobile, processados por Lambda, armazenados no S3 e persistidos no banco.

Minha stack principal é Java, mas nesta função escolhi Node.js com TypeScript pelo cold start menor e pelo consumo reduzido de memória em um cenário serverless. O README do repositório explica essa e outras decisões de arquitetura.

O que tem de interessante:

- Idempotência no banco: reenvios do mesmo lote não geram duplicatas
- Rede privada sem NAT gateway, usando VPC endpoints para S3 e Secrets Manager
- Migrações de banco executadas por uma Lambda dentro da VPC
- Pipeline de deploy pelo GitHub Actions com OIDC, sem chaves AWS guardadas no GitHub
- 25 testes unitários e 8 testes de integração com PostgreSQL real
- Ambiente local com Docker Compose, para rodar tudo sem conta na AWS

Tecnologias: TypeScript, Node.js 22, AWS Lambda, API Gateway, S3, RDS PostgreSQL, Secrets Manager, Terraform, GitHub Actions, Docker.

## Stack

| Área | Tecnologias |
| --- | --- |
| Backend | Java (8 a 21), Spring Boot, Spring Data JPA, Hibernate, Node.js, AdonisJS, PL/SQL |
| Cloud (AWS) | EC2, Lambda, S3, RDS, IAM, Systems Manager, Load Balancer, Route 53, SQS |
| DevOps | GitHub Actions, CI/CD, Docker, Linux, Git, Terraform |
| Frontend | React.js, TypeScript, JavaScript, HTML, CSS |
| Bancos de dados | MySQL, PostgreSQL, Oracle, Amazon RDS |
| Mobile | Android (Java), Flutter, Dart |

## O que já entreguei no trabalho

Na Usina São Domingos, desde março de 2024, primeiro como Assistente de T.I. e hoje como Analista de Sistemas Júnior.

**Backend e modernização de sistemas legados**

- Liderei a refatoração de um sistema legado de VRaptor para Spring Boot, com arquitetura modular que reduziu o tempo de onboarding de novos desenvolvedores e acelerou as entregas
- Liderei a migração do backend de AdonisJS 4 (JavaScript) para AdonisJS 5 com TypeScript, adotando tipagem estática para facilitar a manutenção
- Desenvolvo e mantenho APIs RESTful em Java e Spring Boot que integram sistemas corporativos em produção
- Liderei a migração completa do código do app mobile para AndroidX, deixando o aplicativo disponível para 100% da frota de dispositivos da empresa e reduzindo custos de compra de hardware

**Cloud e infraestrutura na AWS**

- Implementei o pipeline de CI/CD com GitHub Actions e SSM, reduzindo o deploy de cerca de 5 minutos, feito manualmente, para poucos segundos
- Implementei acesso seguro ao banco de dados por túnel SSM, eliminando a dependência de um bastion com lista fixa de IPs, com gestão de usuários e policies no IAM
- Criei, configurei e fiz deploy em instâncias EC2 (Node.js, backend Java e Tomcat)
- Configurei Target Group, Load Balancer e Route 53 para expor uma aplicação interna com endereço fixo e acesso externo estável

**Dados e automação**

- Criei e liderei tecnicamente uma função Lambda que recebe dados de aplicações mobile, envia ao S3, processa as informações e grava no banco, eliminando um processo manual
- Participei da migração de MySQL para Amazon RDS, do planejamento aos testes e à validação
- Trabalhei na integração de dados entre MySQL e Oracle, garantindo consistência entre os sistemas

**Aplicações full stack e mobile**

- Desenvolvi o Sistema de Agendamento de Cargas (React, Java e MySQL), que eliminou 100% dos conflitos de agenda e reduziu o tempo médio de espera no pátio logístico
- Desenvolvi dashboards web em React com cadastro, edição, exclusão e replicação de dados
- Desenvolvi soluções mobile com Android (Java) e Flutter/Dart

## Contato

- LinkedIn: [linkedin.com/in/ehfcaro](https://linkedin.com/in/ehfcaro)
- E-mail: eduardofreitascaro@gmail.com
