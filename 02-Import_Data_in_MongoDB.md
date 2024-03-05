## ⌛ Importing Data into MongoDB using mongoimport
---

1. **Download MongoDB Database Tools:**

- Visit the [MongoDB Download Center](https://www.mongodb.com/try/download/database-tools) to download the MongoDB Database Tools.

2. **Import JSON Data:**
  - Use `mongoimport` to import JSON data into a MongoDB collection.
    ```bash
    mongoimport --db <database_name> --collection <collection_name> --file <path_to_json_file> 
    ```
    Replace `<database_name>`, `<collection_name>`, and `<path_to_json_file>` with appropriate values.
    
  - If your JSON file contains an array of JSON documents, use the `--jsonArray` option:
     ```bash
    mongoimport --db <database_name> --collection <collection_name> --jsonArray --file <path_to_json_file> 
    ```
    Replace `<database_name>`, `<collection_name>`, and `<path_to_json_file>`
     
3. **Import CSV Data:**
  - Use `mongoimport` to import CSV data into a MongoDB collection:
    ```bash
    mongoimport --db <database_name> --collection <collection_name> --type csv --headerline --file <path_to_csv>
    ```
    Replace `<database_name>`, `<collection_name>`, and `<path_to_csv_file>` with appropriate values.

---
