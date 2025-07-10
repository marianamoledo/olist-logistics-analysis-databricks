# projeto-olist

## Introdução

Oi :) 

O que vou tentar fazer nesse projeto é analisar dados reais de um marketplace brasileiro para investigar o desempenho logístico nas entregas de pedidos realizados entre 2016 e 2018.

Com base na base pública da Olist, disponibilizada no Kaggle, serão exploradas métricas relacionadas a tempo de entrega, atrasos e satisfação dos clientes. A partir dessa análise, espero conseguir gerar insights sobre a eficiência da operação logística em diferentes regiões do Brasil.

Vou realizar a análise utilizando:

- **Databricks** para ingestão, processamento e modelagem dos dados
- **Python + SQL (PySpark)** para tratamento e cálculo das métricas
- **Power BI** para visualização dos resultados

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

- **Schema**: `default`
- **Formato**: Tabelas gerenciadas (Databricks Tables)

As tabelas foram automaticamente reconhecidas e estruturadas com base no cabeçalho dos arquivos :)

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
