# Dollar_Project
This project aims to execute an extract, transform, and load (ETL) process by extracting the daily dollar exchange rate from the Banco Central do Brasil (BACEN) API.\
The raw data will be stored in CSV format in the data lake, and the curated data will be stored in a database.

## 1 - Business Rules
- The pipeline must run every day at 9 a.m. to extract data from the previous day.
- Raw data must be saved in parquet format in the data lake, with the file name corresponding to the date it refers to.
- Data must be refined and inserted into a table in the database.

**Data Source and Specification**
- Data should be extracted from the following BACEN link: (https://olinda.bcb.gov.br/olinda/servico/PTAX/versao/v1/odata/CotacaoDolarPeriodo(dataInicial=@dataInicial,dataFinalCotacao=@dataFinalCotacao)?@dataInicial=%2701-01-2019%27&@dataFinalCotacao=%2712-31-2025%27&$top=9000&$format=text/csv&$select=cotacaoCompra,cotacaoVenda,dataHoraCotacao)

## 2 - Architecture Model
For this project the following tools were used:
- Azure Data Lake Storage (ADLS) for store the raw data;
- Azure Databricks for data transformation;
- Azure Data Factory for orchestration;
- Azure SQL Database for the silver layer storage;
- Azure Key Vault to safely store the keys and passwords used in this project;
- GitHub for documentation and code versioning

  ![dolar_architecture drawio](https://github.com/Ingrid-Sollim/Projeto_dolar/assets/119446486/470f441f-c978-4475-8d39-1533b203e46c)



## 3- Development process to the final stage
# 3.1 - Data Pipeline
A pipeline was created using Azure Data Factory(ADF). In order to update the database daily, a trigger was created to run the pipeline every day at 09:00h.\

![trigger](https://github.com/Ingrid-Sollim/Projeto_dolar/assets/119446486/a4fbdccd-b7f2-4e07-b002-2a2d55d2380b)

In order to connect Databricks the ADF, a linked service was created. To create it a Databrick Workspace URL was needed and the access token. \
![azurelinkedservice](https://github.com/Ingrid-Sollim/Projeto_dolar/assets/119446486/347dc854-0fda-4fbe-8445-4b32508a92e7)


The pipeline has two tasks, the first consists of a notebooks that extracts the data from API and stores it in the Data Lake in the parquet format.\
The second notebook reads the parquet file, cleans the data and change the columns to decimal and timestamp.


![dolar_adf](https://github.com/Ingrid-Sollim/Projeto_dolar/assets/119446486/19fd496e-e7c8-484e-9a8b-16c1674c40d8)

