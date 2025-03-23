# NBA_DATA_LAKE_AZURE
Certainly! Below is a clean and detailed Medium post outlining the steps, files, authentication, and commands to run the project.

---

# **Setting Up an NBA Data Lake on Azure: A Complete Guide**

In this guide, we'll walk you through the process of setting up an NBA Data Lake on **Microsoft Azure** using Python. We will be creating a **Storage Account** and a **Synapse Workspace**, fetching NBA data from the **SportsData.io** API, and uploading it into Azure Blob Storage. By the end of this tutorial, you'll have a fully functional Data Lake that can store and process NBA data.

## **What We'll Achieve in This Project**

1. **Azure Resource Setup**: Create a Storage Account and Synapse Workspace in Azure to hold and analyze NBA data.
2. **NBA Data Integration**: Fetch real-time NBA data from the **SportsData.io** API.
3. **Data Storage**: Upload the fetched data to an Azure Blob Storage container.
4. **Automation**: Use Python scripts to automate the resource creation and data upload processes.

## **Prerequisites**

Before starting, ensure you have the following:

1. **Azure Account**: If you don’t have an Azure account yet, [sign up for one here](https://azure.microsoft.com/en-us/free/).
2. **SportsData.io Account**: You will need an account at [SportsData.io](https://sportsdata.io/) to access the NBA data API.
3. **Python 3**: Ensure Python 3 and `pip` are installed on your system. You can check if Python is installed by running:
   ```bash
   python3 --version
   pip --version
   ```
   If not, [download Python 3](https://www.python.org/downloads/).
4. **Dependencies**: We will install the required Python libraries, which are listed in the `requirements.txt` file.

## **Link to the Repo**

We’ll be working with the following repository for this project:
[GitHub Repo: Azure-30day--DevOps-Challenge - Week1 - AzureDataLake](https://github.com/alahl1/Azure-30day--DevOps-Challenge/tree/main/Projects/Week1/AzureDataLake)

---

## **Files Used in This Project**

The project consists of several Python files that automate the creation of Azure resources, fetch NBA data, and upload it to Azure Blob Storage. Below is a breakdown of each file and its role:

### **1. `resource_manager.py`**

This file handles the creation of **Azure resources** (like Storage Accounts and Synapse Workspaces). It includes functions for:
- Creating a **Resource Group** (if not already present).
- Creating an **Azure Storage Account** and returning its connection string.
- Creating a **Synapse Workspace** and returning its SQL endpoint.

It uses the **Azure SDK** to interact with Azure services.

### **2. `data_operations.py`**

This file is responsible for:
- **Fetching NBA data** from the **SportsData.io** API.
- **Uploading the data** to Azure Blob Storage, ensuring the data is stored in line-delimited JSON format.

It makes use of the **requests** library to interact with the SportsData.io API and the **Azure Blob Storage SDK** to upload the data.

### **3. `setup_nba_data_lake.py`**

This is the main script that:
1. Creates the necessary Azure resources (Storage Account and Synapse Workspace) using the functions from `resource_manager.py`.
2. Fetches NBA data using `data_operations.py`.
3. Uploads the data to Azure Blob Storage.

This script also writes the **connection details** (such as connection strings and SQL endpoint) to the `.env` file for future use.

### **4. `.env` (Environment File)**

The `.env` file contains the **credentials** required for authentication with both Azure and the SportsData.io API. It helps keep sensitive data (like API keys and login credentials) secure and ensures that you can dynamically access them in the Python scripts.

#### Sample `.env` file:
```ini
# SportsData.io configurations
SPORTS_DATA_API_KEY=YOUR-API-KEY
NBA_ENDPOINT=https://api.sportsdata.io/v3/nba/scores/json/Players

# Azure Configurations
AZURE_SUBSCRIPTION_ID=YOUR-AZURE-SUBSCRIPTION-ID
AZURE_RESOURCE_GROUP=YOUR-RESOURCE-GROUP
AZURE_STORAGE_ACCOUNT=YOUR-STORAGE-ACCOUNT-NAME
AZURE_LOCATION=eastus2
AZURE_CONNECTION_STRING=  # Will be dynamically filled
SYNAPSE_SQL_ENDPOINT=     # Will be dynamically filled
SYNAPSE_WORKSPACE_NAME=Your-Synapse-Workspace-Name
SQL_ADMIN_LOGIN=your_admin_user
SQL_ADMIN_PASSWORD=Str0ngPass!123
```

### **How to Set Up Your `.env` File**

You will need to replace the placeholders in the `.env` file with your own credentials:
1. **SportsData.io API Key**: Sign up on [SportsData.io](https://sportsdata.io/) to get an API key.
2. **Azure Credentials**: You’ll need your Azure Subscription ID, Resource Group, Storage Account name, and other details from your Azure account.

---

## **Steps to Run the Project**

### **Step 1: Clone the Repository**

Start by cloning the repository to your local machine:
```bash
git clone https://github.com/alahl1/Azure-30day--DevOps-Challenge.git
cd Azure-30day--DevOps-Challenge/Projects/Week1/AzureDataLake
```

### **Step 2: Install Dependencies**

Install the necessary Python dependencies using `pip`:
```bash
pip install -r requirements.txt
```

### **Step 3: Set Up the `.env` File**

Create a `.env` file in the project root directory and add your credentials as mentioned in the sample `.env` file.

### **Step 4: Run the Setup Script**

Run the `setup_nba_data_lake.py` script to set up the Azure resources, fetch the NBA data, and upload it to Azure Blob Storage:
```bash
python3 setup_nba_data_lake.py
```

This script will:
1. Create the **Azure Storage Account** and **Synapse Workspace**.
2. Fetch NBA player data from the **SportsData.io** API.
3. Upload the fetched data to **Azure Blob Storage**.

### **Step 5: Verify the Resources**

Log in to your **Azure Portal** and verify that the **Storage Account** and **Synapse Workspace** have been created successfully.

---

## **Conclusion**

Congratulations! By following this guide, you’ve successfully set up an **NBA Data Lake on Azure**, fetched data from the **SportsData.io API**, and uploaded it into **Azure Blob Storage**. You’ve also automated the process using Python scripts.

This setup serves as a foundation for more complex data analytics or machine learning projects on NBA data, all within the powerful ecosystem of **Azure**.

---

### **Thank You and Happy Learning!**

Thank you for following this tutorial. I hope you found it helpful! If you have any questions or run into issues, feel free to reach out. Wishing you happy learning and best of luck with your data lake setup!

---

