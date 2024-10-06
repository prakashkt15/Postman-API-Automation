# Postman API Testing Framework with Newman Integration
This README provides instructions on how to install and use Newman to execute Postman collections from the command line.

## Project Overview
This repository contains two distinct projects:
1. **Simple Grocery Store API** 
2. **Trello API**

### 1. Simple Grocery Store API
**Description**:  
The Simple Grocery Store API provides endpoints for managing grocery items, categories, and stock levels in a grocery store.
For more details, visit the [Simple Grocery Store API documentation](https://github.com/vdespa/Postman-Complete-Guide-API-Testing/blob/main/simple-grocery-store-api.md).

### 2. Trello API
**Description**:  
The Trello API allows users to manage boards, lists, and tasks similar to Trello. It provides endpoints for creating, updating, and deleting these resources.  
For the full Trello API documentation, refer to [Trello API Documentation](https://developer.atlassian.com/cloud/trello/rest/api-group-actions/#api-group-actions).

**Generating API Key and Token**:  
To create a token and key for accessing Trello APIs, please follow these steps:
- Read this guide on [Trello API Introduction](https://developer.atlassian.com/cloud/trello/guides/rest-api/api-introduction/).
- Follow the steps on [Trello Power-Ups Admin](https://trello.com/power-ups/admin) to generate your API key and token.


--- 
## Installation
### Prerequisites
- **Install Node.js**: Download from [Node.js official website](https://nodejs.org/) and follow the installation instructions.

To install Newman globally, use the following command:
```bash
npm install -g newman 
```

To install the Newman HTML Extra Reporter, use the following command:
```bash
npm install -g newman-reporter-htmlextra
```
## Importing a Collection from GitHub
To import a Postman collection using GitHub cloning:
1. Clone the repository to your local machine using the following command:
    ```bash
    git clone https://github.com/prakashkt15/Postman-API-Automation.git
    ```
2. Navigate to the cloned repository directory: 
    ```bash
    cd Postman-Complete-Guide-API-Testing
    ```
3. Locate the collection JSON file (e.g., simple-grocery-store-api.json).
4. Open Postman and click on Import.
5. In the Import window, select the Upload Files tab and choose the JSON file you located.

## Executing Postman Collections with Newman
You can execute a Postman collection using Newman in two ways: by referencing a local JSON file or by using a public link.

### Option 1: Running a Local Collection
Export your collection from Postman as a JSON file and save it to your local system.
Use the following command to run the collection:
```bash
newman run "collectionName.json" --folder "folder name" -e "env variable name" -g "global variable name" -d "filename.json"
```
```bash
Example:
newman run "myCollection.json" --folder "UserManagement" -e "environment.json" -g "global.json" -d "dataFile.json"
```

To generate both console and HTML reports when running a local collection:
```bash
newman run "myCollection.json" --folder "UserManagement" -e "environment.json" -g "global.json" -d "dataFile.json" -r cli,htmlextra
```

### Option 2: Running a Collection via Public Link
Get a public link to your collection by clicking on the Share button in Postman.
Use the following command format to execute your collection directly from the link:
```bash
newman run <collection_url> --folder "<folder_name>" -e <environment_url> -g <global_url> -d <data_file.json>
```
```bash
Example:
newman run https://api.getpostman.com/collections/<collection_id>?apikey=<your_api_key> \
--folder "UserManagement" \
-e https://api.getpostman.com/environments/<environment_id>?apikey=<your_api_key> \
-g https://api.getpostman.com/globals?apikey=<your_api_key> \
-d data_file.json
```    
To generate both console and HTML reports when running a collection from a public link:
```bash
newman run https://api.getpostman.com/collections/<collection_id>?apikey=<your_api_key> \
--folder "UserManagement" \
-e https://api.getpostman.com/environments/<environment_id>?apikey=<your_api_key> \
-g https://api.getpostman.com/globals?apikey=<your_api_key> \
-d data_file.json \
-r cli,htmlextra
```