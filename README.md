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
2. Capa Bronze: Almacenar datos en tabla delta con información sin transformar, sin validación y respetando datos de origen
3. Capa Silver: Almacenar datos en tablas delta con información procesada y aplicando transformación de datos, normalización y completitud.
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
   
3. SILVER:
   • Eval_set: catalogo de datos
   • order_products: union de origenes de datos prior y train
   • orders: datos de ordenes con identificador de usuario y tiempos en horas y días desde el registro de orden
   • kpis_products_ordered: obtiene indicador del total de ordenes por departamento, pasillo y producto
   • kpis_eval_set: indicadores del total de usuarios, total de ordenes y promedios dehoras y días desde el registro de orden
   
6. GOLD:

   • kpis_products_ordered: obtiene indicador del total de ordenes por departamento, pasillo y producto
   • kpis_eval_set: indicadores del total de usuarios, total de ordenes y promedios dehoras y días desde el registro de orden

# Estructura del proyecto

Proyecto ETL Databricks/

1. .github:
  1.1 workflows:
    1.1.1 deploy-notebook.yml

2. Dashboard:
   2.1 Supermarket Superstore.pbix
   
3. Dataset:
    3.1  Aisles.csv
    3.2  order_products__prior.csv
    3.3 order_products__train.csv
    3.4 orders.csv
    3.5 products.csv
    3.6 sample_submission.csv
    3.7 deparments.csv
   
4. Evidencias
5. Preparacion ambiente:
    5.1 1. Preparacion_Ambiente.ipynb
    5.2 2. DDLs Tablas.ipynb
6. Proceso:
    6.1 1. Preparacion_Ambiente.ipynb
    6.2 2. DDLs Tablas.ipynb
    6.3 3. Ingesta bronze.ipynb
    6.4 4. Transformacion.ipynb
    6.5 5. Load.ipynb
    6.6 6. Grants.ipynb
7. Reversion:
    7.1 Reversion.ipynb
8. Seguridad:
    8.1 Grants.ipynb
8. README.md

# Tecnologías

1. Azure Databricks
2. Azure
3. Azure Data Factory
4. PySpark
5. DeltaLake
6. Azure SQL Database
7. CI/CD Github Actions
8. Azure Key Vault

# WorkFlow Databricks
<img width="1906" height="724" alt="Job_pipeline_databricks_productivo" src="https://github.com/user-attachments/assets/b7ce6518-e0ad-49a4-99a5-c766e039caf6" />

# Pipeline Azure Data Factory
<img width="1910" height="942" alt="Ejecución_pipeline_data_factory" src="https://github.com/user-attachments/assets/40a54d2c-6bea-4d78-90e9-9759906ab988" />

# Dashboard Power BI

1. Vista departamento
<img width="1918" height="1024" alt="Dashboard_deparments" src="https://github.com/user-attachments/assets/75545ee3-b3d4-496b-b84a-84cdfcb4ced7" />

3. Vista pasillos
<img width="1920" height="1024" alt="Dashboard_aisles" src="https://github.com/user-attachments/assets/3c21b328-b9b8-4c73-baed-657176926af5" />

5. Vista Productos
<img width="1916" height="1022" alt="Dashboard_products" src="https://github.com/user-attachments/assets/a5dd4968-02ed-4ad5-9632-2cdd8e50ee44" />

# Autor




  

