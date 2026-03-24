# Supermarket Superstore Dataset-Bundle ETL Databricks

Proceso ETL Databricks utilizando arquitectura medallion:

  • Databricks
  • Azure
  • Azure Data Factory
  • PySpark
  • DeltaLake
  • Azure SQL Database
  • CI/CD Github Actions

## Descripción:

Proceso ETL que extrae información de DataLake y Azure SQL Database con datos que proveen información relacionada con laa ventas de supermecado y sus transacciones:

  • Ventas de supermercado
  • Productos
  • Ordenes
  • Departamentos
  • Entre otros archivos CSV como prioridad de ordenes de productos, orden de entrenamiento de productos
  
### Características

1. Arquitectura medallion: Capas RAW, Bronce, Silver y Gold.
2. Azure Datafactory: orquestación de pipeline para la ejecución de proceso ETL con notebooks de Databricks
3. Azure SQL Database: Estracción de datos y almacenamiento final en base de datos que consume el Dashboard en Power BI
4. GitHub Actions: Workflow para despliegue de Desarrollo a productivo (CICD) usando YAML
5. Dashboard Power BI: implementación de tablero que consume los indicadores generados en el proceso ETL
6. Unit Catalog: administracción de catalogos, esquemas, roles y usuarios en toda la arquitectura medallion
7. Azure Key Vault: para garantizar el usos de secretos y claves aplicadas en la arquitectura, asegurando la gestión de datos sensibles como password y tokens.

# Descripción Arquitectura

1. Capa RAW: Uso de azure data lake para almacenar archivos CSV y azure SQL database para origenes de datos.
2. Capa Bronze: Almacenar datos en tabla delta con información sin transformar
3. Capa Silver: Almacenar datos en tablas delta con información procesada y aplicando transformación de datos.
4. Capa Gold: Almacenar datos de indicadores y agregaciones para desarrollo de insights
5. Base de datos intermedia: Base de datos en azure SQL Database para guardar indicadores que consumiran usuarios y dashboard de Power BI
6. Talero de datos: Dashboard en Power BI para mostrar indicadores

# Estructura pipeline ETL

1. RAW:
   • Aisles.csv
   • order_products__prior.csv
   • order_products__train.csv
   • orders.csv
   • products.csv
   • sample_submission.csv
   • deparments (tabla en azure sql database)

2. BRONZE:
   • Aisles
   • order_products__prior
   • order_products__train
   • orders
   • products
   • sample_submission
   • deparments
   
4. SILVER
5. GOLD

# Tecnologías


  

