# Contoso Finance

- Contoso Finance is a N-tier application. A frontend, API and a database
- This is a script that creates the needed services on Azure to host the Contoso Finance

- Reference steps can be found [here](https://github.com/apwestgarth/MCW-Azure-Stack/blob/02c421eb5e3ae7af1da11f35ba167e6cd3e68958/Hands-on%20lab/HOL%20step-by-step%20-%20Azure%20Stack.md) 


### Task 1: Create SQL Hosting Server

#### Tasks to complete

-   Create a new SQL Hosting Server in the Azure portal. During creation, set the size of the new hosting server in GB to 100.

#### Exit criteria

-   You should have a new SQL Hosting Server resource provisioned in the Azure portal

#### Tasks to complete

-   Deploy a new Azure SQL Database instance in the Azure portal using the following configuration:

    -   Database Name: **ContosoFinanceWebDB**

    -   Max Size in MB: **250**

    -   Resource group: **ContosoFinanceApp**

    -   Location: **Local**

-   Copy the connection string for later reference

#### Exit criteria

-   A deployed SQL Database in the Azure portal portal and a copy to the connection string

## Exercise 3: Deploy Contoso Financial Web Application

Duration: 15-30 minutes

In this exercise, you will provision a website using the Azure portal. The Web App will leverage the SQL DB running in Azure. This is the front-end website that customers will see when browsing for a Mortgage or other financial services products.

### Task 1: Create the Web App

#### Tasks to complete

-   Create a new Azure Web App in the Azure portal portal using the following configuration:

    -   App Name: **Specify a unique and valid URL (until the green check mark appears)**

    -   Resource group: **ContosoFinanceApp**

#### Exit criteria

-   A functioning web app deployed in the Azure portal portal

### Task 2: Provision an Azure Storage Account

#### Tasks to complete

-   Create a new Azure Storage Account in the Azure portal portal using the following configuration:

    -   Name: **unique value for the storage account (ensure the green check mark appears)**

    -   Resource Group: **ContosoFinanceApp** 

#### Exit criteria

-   A storage account deployed in the Azure portal Portal

### Task 3: Update the configuration strings

#### Tasks to complete

-   Add a new **App setting** with the following values:

    -   Key: **AzureQueueConnectionString**

    -   Value: **enter the Connection String for the Storage Account that was just created**

-   Locate **Connection Strings** below App settings in the Azure Global Add a new **Connection String** with the following values:

    -   Name: **ContosoFinance**

    -   Value: **enter the Connection String for the SQL Database in Azure you just updated**

    -   Type: **SQL Database**

#### Exit criteria

-   The application settings for the web app should be configured to reference the newly created storage account and Azure SQL Database

### Task 4: Publish the Contoso Financial Web Application

#### Tasks to complete

-   Deploy the web app from the following GitHub repository: <https://github.com/wshamroukh/contosofinanceweb>

#### Exit criteria

-   Navigate to the URL of your Azure Web App and click the Products link. The products catalog should load.

**Note:** You may get an error about CORS. This can be ignored, as it will be configured later in the lab.

## Exercise 4: Deploy the customer offers Web API

Duration: 15-30 minutes

In this exercise, you will provision an Azure API App using the Azure portal. This API application is part of the front-end Web Applications and makes recommendations to the user on products the company wishes to highlight. The API App will leverage the SQL Database deployed previously.

### Task 1: Provision the offers Web API App

#### Tasks to complete

-   Create a new Azure API App using the same resource group as the web app

-   Configure Cross-Origin Resource Sharing (CORS) on the new app to use **ALLOWED ORIGINS**

#### Exit criteria

-   The new API app should be deployed in the same resource group as the web app

-   CORS should configured to allow all origins for the API app

### Task 2: Deploy the Contoso.Apps.Financial.Offers project

#### Tasks to complete

-   Deploy the following application to the new API App: <https://github.com/wshamroukh/contosofinanceoffers>

#### Exit criteria

-   The API app should be populated with the code from the GitHub repository

### Task 3: Update the Configuration Settings with the API URL

#### Tasks to complete

-   Add a new App Setting with the following values:

    -   Key: offersAPIUrl

    -   Value: enter the HTTPS URL for the Offers API App with /api/get appended to the end
    
    Example: https://contosofinanceapi.azurewebsites.net/api/get

#### Exit criteria

-   The web app should now show special offers when loaded from the home page

## Exercise 5: Automating backend processes with Azure functions 

Duration: 15-30 minutes

Contoso wants to automate the process of generating applications in PDF format and using Azure Functions. In this exercise, you will provision a Function App using the Azure portal. This Function App will watch the Azure Storage Queue for a message that the web application has submitted, process the application creating a PDF and storing it in Azure Blob Storage.

### Task 1: Create an Azure function to generate PDF receipts

#### Tasks to complete

-   Create a new Azure Function in the Azure portal portal using the same resource group as the web app

-   Deploy the code from the following repository: <https://github.com/wshamroukh/contosofinancefunction>

-   Scroll down to the **Application settings** and click **+Add new setting** to add a storage connection. This storage account will be used to write the PDFs to blob storage.

    -   Name: **contosofinancestorage (must be this name exactly)**

    -   Value: **paste the connection string for the storage account created earlier in the lab**

-   Locate **Connection Strings** below Application settings, and click **+Add a new** **Connection String** with the following values:

    -   Name: **ContosoFinance (must match exactly -- case sensitive)**

    -   Value: **enter the Connection String for the SQL Database**

-   Type: **SQL Azure**

#### Exit criteria

-   The function code should be deployed and configured to connect to the Azure SQL Database and the Storage Account for the Contoso Web App

## Exercise 6: Deploy Contoso Finance Admin website

Duration: 15-30 minutes

In this exercise, you will provision the admin website to be used by employees to review applications submitted.

### Task 1: Provision the Contoso Finance Admin Web App

#### Tasks to complete

-   Create a new web app in the Azure portal portal that will be used for the admin web app

-   Add a new connection string so it can connect to the Azure SQL Database for the web app

    -   Name: **ContosoFinance**

    -   Value: **enter the Connection String for the SQL Database**

    -   Type: **SQL Database**

#### Exit criteria

-   The web app should be deployed with the connection string configured correctly in application settings

### Task 2: Deploy the call center admin Web App from Visual Studio

#### Tasks to complete

-   Deploy the web app from the following GitHub repository: <https://github.com/wshamroukh/contosofinanceadmin> to the newly deployed web app

#### Exit criteria

-   The web app should load, and any orders that are submitted through the web app should show in the admin portal with the ability to download the PDF

## After the hands-on lab 

Duration: 10 minutes

1.  If provisioned using the Azure Developer Kit in an Azure VM, delete the resource group your Azure Host VM is running in.

2.  If running on your own Developer Kit, delete all resource groups from the Azure portal that you created during the execution of this lab.

You should follow all steps provided *before* performing the Hands-on lab.