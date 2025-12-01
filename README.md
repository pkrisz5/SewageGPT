# SewageGPT

SewageGPT is a customized ChatGPT that is connected with a PostgreSQL database containing information about metagenomic analysis of sewage samples.

Publication:

* Ágnes Becsei, József Stéger, Dávid Visontai, Patrick Munk, Frank M. Aarestrup, István Csabai & Krisztián Papp: **A case study using sewage metagenomic data for assessment of text-to-SQL capabilities in large language models** *Scientific Reports:* https://www.nature.com/articles/s41598-025-28341-7

## Configuration of web-based customized ChatGPT 

Configuration page: https://chatgpt.com/

### Name
* SewageGPT

### Description
* Sewage metagenomics is a powerful tool for the proactive surveillance of potential pathogens and disease outbreaks. Sewage samples from Copenhagen, Rotterdam, Budapest, Rome, and Bologna underwent metagenomic sequencing and results were stored in a database that is reachable with this GPT.

### Instructions
* The GPT should construct SQL queries that answer the user's questions and also need to run it. The "Knowledge" part contains 5 files. The "table_column_description.tsv" file includes a description of columns.  The "table_description.tsv" file contains a description of tables. The "schema.sql" is the schema of SQL database. The "sewage_data_descriptor.txt" contains background information about the dataset. For the construction of SQL query be careful, each table is in the "distilled" schema. The "extra_info.txt" file contains supplementary information that can be useful to construct correct SQL queries. Whenever you connect to the database and send an SQL query, then always include exactly the original question as a comment at the end of the SQL query.

### Knowledge
* Uploaded files are in `uploaded_files` folder. As extra information about the dataset, the Becsei et al. submitted 2025 paper was also included.

### Capabilities
* Web Search
* DALL·E Image Generation
* Code Interpreter & Data Analysis

### Actions

```
{
  "openapi": "3.1.0",
  "info": {
    "title": "Sewage database",
    "description": "Retrieves data from Sewage database",
    "version": "v1.0.0"
  },
  "servers": [
    {
      "url": "https://k8plex-veo.vo.elte.hu/notebook/report/ezc9v9-api"
    }
  ],
  "paths": {
    "/sewage": {
      "get": {
        "description": "GET Sewage data using SQL query",
        "operationId": "getData",
        "parameters": [
          {
            "name": "sql",
            "in": "query",
            "description": "SQL query",
            "required": true,
            "schema": {
              "type": "string"
            }
          }
        ],
        "deprecated": false
      }
    }
  },
  "components": {
    "schemas": {}
  }
}
```
