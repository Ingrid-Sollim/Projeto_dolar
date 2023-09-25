# Dollar_Project
This project aims to extract the daily dollar exchange rate from the Banco Central do Brasil (BACEN) API.\
The raw data will be stored in CSV format in the data lake, and the curated data will be stored in a database.

## 1 - Business Rules
- The pipeline must run every day at 9 a.m. to extract data from the previous day.
- Raw data must be saved in CSV format in the data lake, with the file name corresponding to the date it refers to.
- Data must be refined and inserted into a table in the database.

**Data Source and Specification**
- Data should be extracted from the following BACEN link: (https://olinda.bcb.gov.br/olinda/servico/PTAX/versao/v1/odata/CotacaoDolarPeriodo(dataInicial=@dataInicial,dataFinalCotacao=@dataFinalCotacao)?@dataInicial=%2701-01-2019%27&@dataFinalCotacao=%2712-31-2025%27&$top=9000&$format=text/csv&$select=cotacaoCompra,cotacaoVenda,dataHoraCotacao)

## 2 - Architecture Model

