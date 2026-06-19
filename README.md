# bootcamp_desafio_ec2_aws
Repositório para o desafio sobre gerenciamento de instâncias EC2 na AWS.
# Plataforma de Dados para Análise de Vendas de E-commerce na AWS

## Visão Geral

Este projeto apresenta uma arquitetura de dados baseada em serviços AWS para armazenamento, processamento, análise e visualização de informações de vendas de um e-commerce.

A solução foi projetada para atender desde as necessidades operacionais da aplicação até análises avançadas de Data Science e disponibilização de indicadores para áreas de negócio.

## Objetivos

* Armazenar transações de vendas de forma segura e persistente.
* Centralizar os dados históricos em um Data Lake.
* Disponibilizar dados tratados para análises corporativas.
* Permitir a criação de modelos preditivos utilizando Machine Learning.
* Disponibilizar dashboards e indicadores para as equipes de vendas.

## Arquitetura

### Camada de Aplicação

A aplicação de e-commerce é hospedada em uma instância Amazon EC2.

Os dados transacionais são armazenados em um volume Amazon EBS anexado à instância, garantindo persistência das informações de vendas, pedidos e logs da aplicação.

**Serviços utilizados:**

* Amazon EC2
* Amazon EBS
* Amazon VPC
* Security Groups

### Camada de Data Lake

Os dados operacionais são extraídos periodicamente por funções AWS Lambda e armazenados em um Data Lake no Amazon S3.

O ambiente é organizado em duas zonas:

* Raw: dados brutos
* Curated: dados tratados e padronizados

**Serviços utilizados:**

* AWS Lambda
* Amazon S3

### Camada de Engenharia de Dados

Os dados armazenados no S3 são transformados por processos ETL executados pelo AWS Glue.

Após o tratamento, os dados são disponibilizados para análises em um Data Warehouse Amazon Redshift.

Consultas exploratórias podem ser realizadas através do Amazon Athena.

**Serviços utilizados:**

* AWS Glue
* Amazon Athena
* Amazon Redshift

### Camada de Data Science

O Amazon SageMaker é utilizado para desenvolvimento, treinamento e implantação de modelos de Machine Learning.

Exemplos de aplicações:

* Previsão de vendas
* Segmentação de clientes
* Recomendação de produtos
* Identificação de tendências de compra

Os resultados dos modelos podem ser disponibilizados novamente no Redshift para consumo corporativo.

**Serviço utilizado:**

* Amazon SageMaker

### Camada de Business Intelligence

O Tableau conecta-se ao Amazon Redshift para disponibilizar dashboards e indicadores para as áreas de negócio.

Exemplos de análises:

* Faturamento por período
* Performance de produtos
* Ticket médio
* Conversão de vendas
* Forecast de receita

**Ferramenta utilizada:**

* Tableau

## Fluxo de Dados

1. Clientes realizam compras no e-commerce.
2. A aplicação processa as transações na instância EC2.
3. Os dados operacionais são armazenados em volumes EBS.
4. Funções Lambda transferem os dados para o Data Lake no Amazon S3.
5. O AWS Glue realiza o processamento e tratamento dos dados.
6. Os dados analíticos são carregados no Amazon Redshift.
7. O Amazon SageMaker utiliza os dados para construção de modelos preditivos.
8. O Tableau consome os dados do Redshift e disponibiliza dashboards para os usuários finais.

## Benefícios da Solução

* Arquitetura escalável e baseada em serviços gerenciados.
* Separação entre ambiente transacional e analítico.
* Capacidade de realizar análises avançadas e Machine Learning.
* Disponibilização rápida de indicadores para tomada de decisão.
* Redução do esforço operacional por meio de automação.
