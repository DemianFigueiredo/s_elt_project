
![Vincent Van Joint](image/cannabis2.jpg)

#                         ------ Legalize Cannabis! To be or not to be? ------

This study aims to deliver a DB read to use to analyze the effects of cannabis decriminalization/ legalization for recreational usage on key performance indicators (KPIs) related to homicide victims, prisoner held, drug seizures and addiction treatment in its countries. By using historical data, it will perform Extract-Load-Transform (ELT) processes to define the KPIs for evaluation of the benefits (if any) and consequences of cannabis policy changes.

# Technical Overview

This ETL project focuses on extracting data from multiple sources, enriching and transforming the data, and creating a database using MySQL Workbench to be seeded with the data. The project utilizes various data extraction methods such as archiving, databases and web scraping. The extracted data is then enriched and transformed; and then stored in a MySQL database. 

# Data Extraction

It has used multiple methods to extract data from three different sources as outlined below:

Web Scraping:
Perform web scraping using appropriate libraries or tools, specially BeautifulSoup.
https://en.wikipedia.org/wiki/Legality_of_cannabis

Archive:
All archives were available for extraction as XLSX file, and then converted into CSV  file.
https://dataunodc.un.org/dp-drug-use-treatment
https://dataunodc.un.org/dp-intentional-homicide-victims
https://dataunodc.un.org/dp-drug-seizures
https://dataunodc.un.org/dp-prisons-persons-held
https://dataunodc.un.org/dp-prisons-persons-entering


# Data Transformation
In Jupyter Notebook, used libraries: Pandas, Re, Numpy 

Overall data analysis comprehension: head, shape, info, unique values, duplicate, column titles

Cleansing the data by removing duplicates, null values, or irrelevant information.

Standardizing data formats, units, columns title and index.

Handling missing or incomplete values.

Obs. 1: Data from scraping needed some extra web research for data validation and/or completion. 

Obs. 2: Cleansing of data from ONU’s databases started first in Excel tool since it already came as a complex dataframe (xlsx) by the source; and them final transformation occurred in Jupyter Notebook.

# Database Creation

Creation a database in MySQL Workbench with the extracted and transformed data.

DB creation and Table seeding were done at once using method Table Data Import Wizard.

DataFrame contains 5 tables:

- Table: legal_decrime
    This table contains information about the legal status of cannabis decriminalization or legalization and associated years for each           country.
    Columns:
    o	country_id: The unique identifier for each country.
    o	country: The name of the country.
    o	legal_descriminalized: A flag indicating the legal status of cannabis, where 1 represents decriminalization and 2 represents             legalization.
    o	year_-3 to year_3: Columns for future analysis, indicating years before and after cannabis policy changes. Year_0 equal to year         of law application.

-Table: drug_seizure
    This table stores information about drug seizures, including the drug type, quantity, and associated country.
    Columns:
    o	drug_id: The unique identifier for each drug seizure.
    o	country: The name of the country where the seizure occurred.
    o	drug_group: The category or group to which the drug belongs.
    o	year: The year when the drug seizure took place.
    o	kg: The quantity of drugs seized in kilograms.
 
-Table: prison
    This table maintains information about prison statistics, including the count of prisoners and their associated attributes.
    Columns:
    o	prison_id: The unique identifier for each prison entry.
    o	country: The name of the country to which the prison statistics belong.
    o	indicators: indicators associated with prison [entering in prison/ priosioners on held]
    o	crime_category: The category of crimes for which prisoners are incarcerated.
    o	year: The year of the prison statistics.
    o	count: The count of prisoners for the specific indicator, category and year.

-Table: treat
    This table contains information about addiction treatment statistics, including the count of individuals receiving treatment.
    Columns:
    o	treat_id: The unique identifier for each treatment entry.
    o	year: The year of the treatment statistics.
    o	country: The name of the country where the treatment data is collected.
    o	count: The count of individuals receiving addiction treatment.

-Table: victim
    This table stores information about crimes and victims affected by drug-related or co-related incidents.
    Columns:
    o	vic_id: The unique identifier for each victim/accurance entry.
    o	country: The name of the country where the victimization occurred.
    o	year: The year of the incident.
    o	count: The count of victims or crimes occurrences 

Database creation and seeding saved as .sql files inside folder database.

# Conclusion
This project demonstrates the end-to-end Extract, Transform, Load (ETL) process for data extraction, enrichment, transformation, and database creation. It provides a foundation for further analysis, querying, and visualization of the data stored in the MySQL database.
