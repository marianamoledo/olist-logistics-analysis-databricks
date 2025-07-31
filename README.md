# projeto-olist

## Introdução

Oi :) 

O que vou tentar fazer nesse projeto é analisar dados reais de um marketplace brasileiro para investigar o desempenho logístico nas entregas de pedidos realizados entre 2016 e 2018.

Com base na base pública da Olist, disponibilizada no Kaggle, irei explorar métricas relacionadas a tempo de entrega, atrasos e satisfação dos clientes. A partir dessa análise, espero conseguir gerar insights sobre a eficiência da operação logística em diferentes regiões do Brasil.

## Ferramentas Utilizadas

Vou realizar a análise utilizando:

![Databricks](https://img.shields.io/badge/Databricks-Spark%20Platform-orange?logo=apache-spark&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-003B57?logo=mysql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logo=powerbi&logoColor=black)

- **Databricks Free Edition** para ingestão, processamento e modelagem dos dados
- **Python + SQL (PySpark)** para tratamento e cálculo das métricas
- **Power BI** para visualização dos resultados
---
## Sobre os dados

O conjunto de dados utilizado é o *Brazilian E-Commerce Public Dataset by Olist*, disponível no Kaggle:  
https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data

Os dados contêm informações de pedidos feitos em um marketplace entre 2016 e 2018:
- Informações gerais sobre os pedidos
- Dados dos clientes e vendedores
- Detalhes dos produtos vendidos
- Formas de pagamento utilizadas
- Avaliações dos clientes
- Localização geográfica por CEP
- Traduções das categorias de produto

Essa base é bastante utilizada para estudos sobre comportamento de consumo, logística, avaliação de desempenho, ciência de dados e machine learning.

### Por que escolhi a base da Olist?
Escolhi a base de dados da Olist por ser um exemplo rico e realista de marketplace brasileiro, contendo várias tabelas relacionadas entre si, o que permite explorar diferentes dimensões do negócio, como logística, pagamento, avaliações e localização.

<img width="2486" height="1496" alt="image" src="https://github.com/user-attachments/assets/71b43dd8-164d-46a0-b773-89ac77542275" />

Essa estrutura relacional das tabelas possibilita análises mais completas e realistas, como por exemplo:

- Combinar informações de pedidos com prazos de entrega e localização geográfica.
- Relacionar avaliações dos clientes com os prazos de entrega e forma de pagamento.
- Avaliar o desempenho logístico por região e vendedor.

---

## Camadas do Pipeline de Dados

### 1. Bronze – Ingestão dos Dados Crus

Nesta etapa, carreguei os arquivos `.csv` da base Olist manualmente para o **Databricks Free Edition**, com o objetivo de preservar os dados em seu estado original.  

**Etapas:**
1. Upload dos arquivos `.csv` para um volume do Unity Catalog
2. Registro de cada arquivo como tabela gerenciada no catálogo `olist_database.default`
3. Estruturação automática com base no cabeçalho dos arquivos

<img width="462" height="715" alt="image" src="https://github.com/user-attachments/assets/a636c6c1-c5da-4e7c-821d-06d9bf2f94b2" />

Dessa forma, temos as seguintes tabelas disponíveis:

| Tabela                                 | Origem do CSV |
|----------------------------------------|----------------|
| `olist_customers_dataset`              | Clientes |
| `olist_geolocation_dataset`            | Localização (latitude/longitude por CEP) |
| `olist_order_items_dataset`            | Itens de cada pedido |
| `olist_order_payments_dataset`         | Pagamentos realizados |
| `olist_order_reviews_dataset`          | Avaliações dos clientes |
| `olist_orders_dataset`                 | Dados gerais dos pedidos |
| `olist_products_dataset`               | Informações sobre os produtos |
| `olist_sellers_dataset`                | Dados dos vendedores |
| `product_category_name_translation`    | Tradução das categorias de produtos |

---

### 2. Silver – Tratamento e Enriquecimento
- Cálculo de métricas logísticas:
  - Tempo estimado de entrega
  - Tempo real de entrega
  - Dias de atraso
  - Tempo entre aprovação e envio
- Criação de flags binárias:
  - `fl_delivered`, `fl_on_time`, `fl_late`, etc.
- Criação da tabela `silver_orders`

### 3. Gold – Modelagem Final para Consumo
- Enriquecimento com dados de clientes, localização e produtos
- Colunas auxiliares para filtros e visualização no Power BI (ex: `ano`, `estado`, `categoria`)
- Dados exportáveis para visualização e análise

---




---
