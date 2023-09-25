# Projeto_dolar
Este projeto tem o objetivo de extrair a cotação diária do dolar, a partir dos dados provenientes da API do BACEN.\
Armazenar os dados brutos em formato parquet no Data Lake e armazenar os dados curados em um banco de dados.\

## 1- Regras de negócio
- O pipeline deve rodar todos os dias, às 9h, para extrair os dados do dia anterior; 
- Os dados brutos devem ser salvos em formato csv no Data Lake,com o nome do aquivo sendo a data a que ele se refere;
- Os dados devem ser refinados e inseridos em uma tabela no banco de dados.

**Origem e especificação dos dados**
-Os dados devem ser extraídos do seguinte link do BACEN: [https://olinda.bcb.gov.br/olinda/servico/PTAX/versao/v1/aplicacao#!/]

