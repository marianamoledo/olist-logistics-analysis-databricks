# projeto-olist

## Introdução

Oi :) 

O que vou tentar fazer nesse projeto é analisar dados reais de um marketplace brasileiro para investigar o desempenho logístico nas entregas de pedidos realizados entre 2016 e 2018.

Com base na base pública da Olist, disponibilizada no Kaggle, irei explorar métricas relacionadas a tempo de entrega, atrasos e satisfação dos clientes. A partir dessa análise, espero conseguir gerar insights sobre a eficiência da operação logística em diferentes regiões do Brasil.

Vou realizar a análise utilizando:

## Ferramentas Utilizadas

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

## 🔄 Ingestão dos dados no Databricks

Realizei a ingestão dos dados manualmente, direto na interface do **Databricks Free Edition**, da seguinte forma:

1. Fiz o upload dos arquivos `.csv` para um volume do Unity Catalog
2. Registrei cada arquivo como uma **tabela gerenciada** dentro do catálogo `olist_database`, no schema `default`
3. As tabelas foram automaticamente reconhecidas e estruturadas com base no cabeçalho dos arquivos 
4. A partir daí, os dados podem ser acessados via **SQL Editor** ou com PySpark nos notebooks :)

---

### 🗂️ Tabelas disponíveis

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
## Gerenciamento do Projeto

Criei um board do Github para quem desejar acompanhar as tasks e o progresso do projeto:

[Link para o Board do Projeto](https://github.com/users/marianamoledo/projects/1)

*Em breve: documentação das transformações, cálculos de SLA, métricas e visualizações no Power BI.*
