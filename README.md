# Eduardo Henrique de Freitas Caro

Desenvolvedor Full Stack com foco em backend Java e infraestrutura na AWS, de Catanduva, SP.

Trabalho há mais de 3 anos com Java (Spring Boot), Node.js e React, e gosto de arquitetura backend, design de APIs e nuvem. Hoje sou Analista de Sistemas na Usina São Domingos, onde modernizei sistemas legados, automatizei infraestrutura na AWS e coloquei em produção pipelines de CI/CD. Também estou cursando a pós-graduação em Internet das Coisas no IFSP Catanduva.

## Projeto em destaque

### [Serverless Ingest Pipeline](https://github.com/eduardofcaro1/serverless-ingest-pipeline)

API que recebe lotes de leituras de dispositivos, guarda o payload original no S3, normaliza os dados e grava tudo em PostgreSQL. Roda em AWS Lambda dentro de uma VPC privada, com a infraestrutura definida em Terraform.

É a versão pública e genérica de um padrão que uso no trabalho: dados vindos de aplicações mobile, processados por Lambda, armazenados no S3 e persistidos no banco.

O que tem de interessante:

- Idempotência no banco: reenvios do mesmo lote não geram duplicatas
- Rede privada sem NAT gateway, usando VPC endpoints para S3 e Secrets Manager
- Migrações de banco executadas por uma Lambda dentro da VPC
- Deploy pelo GitHub Actions com OIDC, sem chaves AWS guardadas no GitHub
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

- Migração de um sistema legado de VRaptor para Spring Boot, com arquitetura modular
- Pipeline de CI/CD com GitHub Actions e SSM que reduziu o deploy de cerca de 5 minutos para poucos segundos
- Acesso seguro ao banco por túnel SSM, eliminando a dependência de bastion com lista fixa de IPs
- Função Lambda que recebe dados de aplicações mobile, envia ao S3, processa e grava no banco
- Migração de MySQL para Amazon RDS e migração de AdonisJS 4 para AdonisJS 5 com TypeScript

## Contato

- LinkedIn: [linkedin.com/in/ehfcaro](https://linkedin.com/in/ehfcaro)
- E-mail: eduardofreitascaro@gmail.com
