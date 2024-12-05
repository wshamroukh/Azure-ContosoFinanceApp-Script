# Contoso Finance

- Contoso Finance is a N-tier application. A frontend, API and a database
- This is a script that creates the needed services on Azure to host the Contoso Finance

### Task 1: Create the Web App

1.  From within the Azure tenant portal, click **+Create a resource -\> Web -\> Web App.**

2.  On the **Everything** blade, select **Web App** followed by **Create**.

    ![Screenshot of the Web App option.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image109.png)

3.  On the **Web App** blade, select **App Service plan/Location**.

    ![App Service plan/Location option screenshot](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image110.png)

4.  Create a new App Service plan called **ContosoFinanceWebPlan** with the **D1 Shared** pricing tier and click **OK**.

    ![Screenshot of the D1 Shared pricing tier option.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image111.png)

5.  On the **Web App** blade, specify the following configuration, and click **Create:**.

    -   App Name: **Specify a unique and valid URL (until the green check mark appears)**.

    -   Resource group: **ContosoFinanceWeb**
    -   Application Insights - **Disabled**

        ![Create blade fields are set to the previously defined settings.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image112.png)

### Task 2: Provision an Azure Storage Account

1.  In the Azure Tenant portal, click **+New, Data + Storage,** and **Storage account**.

    ![In the New and Data and Storage blades, the previously defined options are selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image113.png)

2.  On the **Create storage account** blade, specify the following configuration options:

    -   Name: **Unique value for the storage account (ensure the green check mark appears)**.

    -   Resource Group: **AzureGlobalContosoFinance**

        ![Create storage account blade fields are set to the previously defined settings.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image114.png)

3.  Click **Create**.

    ![Create button screenshot](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image115.png)

4.  After the storage account has completed provisioning, open the storage account by clicking **More services,** **Storage accounts**, and storage account name.

5.  On the **Storage** account blade, scroll down, and select the **Access keys** option.

    ![Under Settings, Access keys is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image116.png)

6.  On the **Access keys** blade, click the copy button by **key1** to copy the **Key**. Put the value in notepad for later reference.

    ![The Key 1 copy button is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image117.png)

    ![Key1 displays in Notepad.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image118.png)

7.  On the **Access keys** blade, click the copy button by **key1** on the **Connection string**. Put the value in notepad for later reference.

    ![The Connection string copy button is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image119.png)

    ![In Notepad, the connection string displays.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image120.png)

    > **Note:** If the copy to clipboard button does not work, you may need to highlight the key and copy by right-clicking. Some versions of Internet Explorer have issues with this functionality.

### Task 3: Update the configuration strings

1.  On the left pane of the **contosofinanceweb** Web App, click on **Application settings**.

    ![Under Settings, Application settings is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image121.png)

2.  Scroll down and locate the **App settings** section.

    ![Screenshot of the App settings section.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image122.png)

3.  Add a new **App setting** with the following values:

    -   Key: **AzureQueueConnectionString**

    -   Value: **Enter the Connection String for the Storage Account that was just created**.

        ![Fields in the App settings section are set to the previously defined settings.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image123.png)

4.  Move to your Notepad with the SQL Server Connection string copied from Azure Stack. Update the following items in the string:

    -   Password: **Demo\@pass123**

5.  Locate **Connection Strings** below App settings in the Azure tenant portal, add a new **Connection String** with the following values:

    -   Name: **ContosoFinance**

    -   Value: **Enter the Connection String for the SQL Database in Azure Stack you just updated**.

    -   Type: **SQL Database**

        ![The Connection strings fields display.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image124.png)

6.  Click **Save**.

### Task 4: Publish the Contoso Financial Web Application

1.  From within the web app blade, click on **Deployment Options**.

    ![Deployment options is selected under Deployment.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image125.png)

2.  Click **Choose Source**, and then **External Repository**.

    ![In the Deployment option blade, Choose source is selected. In the Choose source blade, External Repository is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image126.png)

3.  Paste <https://github.com/opsgility/contosofinanceweb> as the **Repository URL** and click **OK**.

4.  Click on the Deployment options button and monitor until the application is deployed.

5.  Click the Overview tab, and then click the URL. You should see the Contoso Finance web app.

    ![The URL is selected in the App Service blade.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image127.png)

    > **Note:** You may get an error about CORS. This can be ignored, as it will be configured later in the lab.

6.  Validate the website by clicking the **Products** link on the menu. If the products return, the connection to the database is successful.

    ![The Products link is called out on the Contoso Finance webpage menu.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image128.png)

## Exercise 4: Deploy the customer offers Web API

Duration: 15-30 minutes

In this exercise, you will provision an Azure API App using the Azure Stack portal. This API application is part of the front-end Web Applications and makes recommendations to the user on products the company wishes to highlight. The API App will leverage the SQL Database deployed previously.

### Task 1: Provision the offers Web API App

1.  Using the Azure Stack Tenant portal, click **+Create a resource**, **Web**, and click **API App**.

    ![Screenshot of the API App button.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image129.png)

2.  Click on **Create**.

3.  On the new **API App** blade, **specify a unique name** for the App Name, and ensure the previously used Resource Group and App Service Plan is selected.

4.  After the values are accepted click **Create**.

5.  On the **App Service** blade, scroll down, and click on **CORS** within the API section of the left pane.

    ![Under API, CORS is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image130.png)

6.  In the **ALLOWED ORIGINS** text box specify \* and click **Save**.

    ![In the App Service blade, Allowed Origins is set to asterisk, and Save is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image131.png)

7.  On the **App Service** blade for the Offers API, click on **Application settings**.

    ![Under Settings in the App Service blade, Application settings is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image132.png)

8.  Scroll down, and locate the **Connection strings** section.

    ![Screenshot of the Connection strings section.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image133.png)

9.  Locate **Connection Strings** below App settings in the Azure global portal.  Add a new **Connection String** with the following values:

    -   Name: **ContosoFinance (must match exactly -- case sensitive)**

    -   Value: **Enter the Connection String for the SQL Database in Azure Stack you just updated**.

    -   Type: **SQL Database**

        ![the Connection strings fields are set to the previously defined settings.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image124.png)

10. Click **Save**.

### Task 2: Deploy the Contoso.Apps.Financial.Offers project

1.  From within the API app blade, click on **Deployment options**.

    ![Under Deployment, Deployment options is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image125.png)

2.  Click **Choose Source**, and then **External Repository**.

    ![In the Deployment option blade, Choose Source is selected. In the Choose source blade, External Repository is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image126.png)

3.  Paste <https://github.com/opsgility/contosofinanceoffers> as the **Repository URL** and click **OK**.

4.  Click on the Deployment options button and monitor until the application is deployed.

5.  On the **Overview** tab, copy the URL for the web app to the clipboard.

### Task 3: Update the Application Settings of the Web App with the API URL

1.  Open the ContosoFinanceWeb application in the Azure Stack Tenant portal and click on Application settings

    ![In the App Service blade, under settings, Application settings is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image134.png)

2.  Scroll down and locate the **App settings** section

    ![Screenshot of the App settings section.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image135.png)

3.  Add a new **App Setting** with the following values:

    -   Key: **offersAPIUrl**

    -   Value: Enter the **HTTPS** URL for the Offers API App with **/api/get** appended to the end.
    
    Example: <https://contosofinanceapi.azurewebsites.net/api/get>

       ![Under App settings, offersAPIUrl and its URL are selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image136.png)

4.  Click on **Save**.

    > **Note:** Ensure the API URL is using **SSL** (https://), or you will see a CORS errors when loading the webpage.

5.  Connect to the URL of the **contosofinanceweb** Web App.

    ![In the App Service blade, the URL link is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image137.png)

6.  On the homepage, you should see the latest offers populated from the offers API.

    ![Screenshot of the Contoso Finance webpage.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image138.png)

## Exercise 5: Automating backend processes with Azure functions 

Duration: 15-30 minutes

Contoso wants to automate the process of generating applications in PDF format and using Azure Functions. In this exercise, you will provision a Function App using the Azure Stack portal. This Function App will watch the Azure Storage Queue for a message that the web application has submitted, process the application creating a PDF and storing it in Azure Blob Storage.

### Task 1: Create an Azure function to generate PDF receipts

1.  From your Azure Stack Host, navigate to the following repository: <https://github.com/opsgility/contosofinancefunction> and click **Clone or download**, and then **Download ZIP**. Download to the **C:\\HOL** folder. After the file is downloaded, right click and extract to **C:\\HOL**.

    ![In the Azure Stack Host, the Clone or download button is selected, and under Clone with HTTPS, the Download ZIP button is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image139.png)

2.  From the Tenant portal, click **+Create a resource**, **Web**, and then click **Function App**.

    ![Function App option screenshot](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image140.png)

3.  Complete the **Create Function App** blade using the following inputs:

    -   App name: **Specify a unique name**.

    -   [Resource Group](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview): **ContosoFinanceWeb**

    -   Hosting Plan: **App Service Plan**

    -   App Service plan/Location: **ContosoFinanceWeb**

    -   Storage Account: **Select your storage account**.

        ![Create blade fields are set to the previously defined settings.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image141.png)

4.  Click **Create**.

5.  Using the Azure Stack portal, open the Function App you just created, click **Functions** and then **New Function**.

    ![The New function button is selected in the Function Apps blade.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image142.png)

6.  Locate the **Queue trigger** box and click **C\#**.

    ![C\# is selected on the Queue trigger page.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image143.png)

7.  Complete the **New Function** blade using the following inputs and click **Create**.

    -   Language: **C\#**

    -   Name: **QueueTriggerGeneratePDF**

    -   Queue name: **receiptgenerator (must be this exact text)**

        ![Fields in the New Function blade are set to the previously defined settings.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image144.png)

8.  Expand the View files area on the right of the code window, and click **Upload**.

    ![In the View files section, Upload is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image145.png)
    
    ![In the View files section, the Upload link is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image146.png)

9.  Upload the following files from your LABVM in the **C:\\HOL\\contosofinancefunction-master** folder:

    -   CreatePdfReport.csx

    -   Project.json

    -   run.csx

    -   StorageMethods.csx

    -   ViewModels.csx

10. Click on **run.csx** to refresh the code editor.

    ![Under View files, run.csx is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image147.png)

11. Select the **name of your function app followed by** **Application settings**.

    ![The previously mentioned settings are selected in the Function Apps blade.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image148.png)

12. Scroll down to the **Application settings** and click **+Add new setting** to add a storage connection. This storage account will be used to write the PDFs to blob storage.

    -   Name: **contosofinancestorage (must be this name exactly)**

    -   Value: **Paste the connection string for the storage account created earlier in the lab**.

13. Locate **Connection Strings** below Application settings in the Azure tenant portal, and click **+Add a new** **Connection String** with the following values:

    -   Name: **ContosoFinance (must match exactly -- case sensitive)**

    -   Value: **Enter the Connection String for the SQL Database**.

    -   Type: **SQL Azure**

        ![Under Application settings, ContosoFinance is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image149.png)

14. Scroll back up to the top of the blade and click **Save**.

    ![The Save button is selected in the Function Apps blade.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image150.png)

## Exercise 6: Deploy Contoso Finance Admin website

Duration: 15-30 minutes

In this exercise, you will provision the admin website to be used by employees to review applications submitted.

### Task 1: Provision the Contoso Finance Admin Web App

1.  In the Azure tenant portal, click **+Create new resources**, **Web**, and select **Web App**.

2.  Specify a **unique URL** for the Web App, ensure the **same App Service Plan** as well as the **ContosoFinanceWeb** resource group you have used throughout the lab are selected.

    ![Fields in the Create blade are set to the previously defined settings.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image152.png)

3.  After the values are accepted, click **Create**.

4.  Navigate to the **App Service** blade for the Admin app recently provisioned.

    ![contosofinanceadmin option screenshot](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image153.png)

5.  On the **App Service** blade, click on **Application settings** in the left pane.

    ![Under Settings, Application settings is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image154.png)

6.  Scroll down and locate the **Connection strings** section.

    ![Screenshot of the App Services blade.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image155.png)

7.  Locate **Connection Strings** below App settings in the Azure tenant portal add a new **Connection String** with the following values:

    -   Name: **ContosoFinance**

    -   Value: **Enter the Connection String for the SQL Database in Azure Stack you just updated**.

    -   Type: **SQL Database**

        ![Connection strings fields screenshot.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image124.png)

8.  Click **Save**.

### Task 2: Deploy the call center admin Web App from Visual Studio

1.  From within the web app blade, click on **Deployment options**.

    ![Under Deployment, Deployment options is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image125.png)

2.  Click **Choose Source**, and then **External Repository**.

    ![In the Deployment option blade, Choose source is selected. In the Choose a source blade, External Repository is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image126.png)

3.  Paste <https://github.com/opsgility/contosofinanceadmin> as the **Repository URL** and click **OK**.

4.  Click on the Deployment options button and monitor until the application is deployed.

5.  On the **Overview** tab, copy the URL for the web app to the clipboard.

6.  Connect to the **contosofinanceadmin** portal to see the list of applications that have been completed.

    ![Screenshot of the Contoso webpage for Contoso Finance Admin.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image156.png)

>**Note**: In production this application would be secured using Azure AD for authentication purposes.

7.  Since the application is fully deployed, you will want to see it work end to end. Open the URL for the contosofinanceweb Web App. The application will load in the browser.

    ![Screenshot of the Contosofinanceweb Web App URL.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image157.png)

    ![Web App webpage screenshot.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image158.png)

8.  Notice how the API application loaded the Today's Offers area. Click through to one of the products and add it to your cart.

    ![Screenshot of the Today\'s Offers webpage area.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image159.png)

9.  Click **Apply**.

    ![Under Product Name, the Apply button is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image160.png)

10. Complete the Application and click **Continue** followed by **Complete Application** on the confirmation screen.

    ![Screenshot of the Contoso Finance application.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image161.png)

    ![Screenshot of the Complete Application button.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image162.png)

11. Now, to act as an employee, open the Admin application to see the submitted applications. Click **Details** on one of the applications.

    ![The URL link is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image163.png)

    ![Screenshot of the Contoso webpage Contoso Finance Admin section.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image164.png)

12. Notice the details of the application. This data is stored in SQL DB running in PaaS on Azure Stack. Click **Download application to view a sample PDF**.

    ![Under Application Details, the Download application link is selected.](https://github.com/apwestgarth/MCW-Azure-Stack/tree/master/Hands-on%20lab/images/Hands-onlabstep-by-step-AzureStackimages/media/image165.png)