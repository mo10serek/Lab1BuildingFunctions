# Lab 1 Building Functions

## Links to other repositories 

[Blob storage binding tutorial](https://github.com/mo10serek/Blob-Storage-Binding-Tutorial)

[SQL Database binding tutorial](https://github.com/mo10serek/SQL-Database-Binding-Tutorial)

## Sign in to Azure

before you run the functions in the links above, you need to sign in to Azure. To do that, install the Azure extension and click **Sign in to Azure** in the **Azure Resources** under **Resources**.

## Creating a Azure Function for each resource

Before you start running, you need to make a function app for each binding application. Press F1 to open the command palette and select **Azure Functions: Create Function App in Azure** and then fill out the following detail:

- **Subscription**: the subscription you usually you use
- **name**: blobstoragebunding or sqldatabasebinding
- **Location**: East US
- **runtime stack**: newest python version (Python 3.12)

Wait until each of the individual resources had been created that are displayed in AZURE: ACTIVITY LOG

After that it will show you all of the resources created. Start running the functions 

### Binding Blob Storage

We start runing the function to bind the blob storage but first weee need to download the function app settings

First press F1 to open the command palette and run `Azure Functions: Download Remote Settings...` and Select **Yet to All** to overwrite the existing local settings

#### Run blob storage binding function

In order to run the blob storage binding function. First you need to start the function app by pressing F5 and right click `HttpExample` function under the `Local Project` section and click `Execute Function Now...`. Then enter the request body by Press `Enter` to send the request message in the function.

#### Connect Storage Explorer

Download `Microsoft Azure Storage Explore` in this link: https://storageexplorer.com/.

After downloading, open the application and click the person icon and click the **Sign in with Azure...** link. 

In the **Connect** window pick **Add an Azure account** and have your Azure environment ready and then sign in. 

Then pick your subscription and select **Open Explorer**

#### Check the Output queue

Go to Visual Studio Code and press F1 to open the command palette and run `Azure Storage: Open in Storage Explorer` and pick your storage account.

If you do that, then it will open your storage account in Azure Storage Explorer. Then open the Queues node and open **outqueue** queue. After that, you will see one message which is "Azure". 

#### Run again and check if the app is updated

Press F1 again to open the command palette and run `Azure Functions: Deploy to function app...`. Choose the function app you made and later select **Deploy** when you are in the redeploying process.

After redeploying, run the `Execute Function Now...` command to run the function.

Check Azure Storage Explorer to see if there is a new message in the queue. After that you successful run the app.

### Binding SQL Queue

Now we need to run the SQL Queue binding function in the other repo.

#### Developed first single database

In Azure Portal, open **Azure SQL** and select `Single database` under Resource type and select `Create` under **SQL Databases**. Fill out the detail for the project

- **Subscription**: (your subscription)
- **Resource group**: (different resource group from the function group)
- **Database name**: mySampleDatabase
- **Server**:
    - **Server name**: pick a unique name
    - **Location**: `West ES`
    - **Authentication method**: Select SQL Server authentication
    - **username**: (your username)
    - **password**: (your password)
- **Want to use SQL elastic pool**: **No**
Go to the network section next:
- **Allow Azure services and resources to access this server**: **Yes**

After filling out the details, select `Create` in the `Review + create` page.

#### adjusting the SQL database

After the SQL database is deployed, get the connection string under **ADO.NET (SQL authentication)** and store it somewhere.

After that, go the Query editor under the database blade and pastes

```
CREATE TABLE dbo.ToDo (
    [Id] UNIQUEIDENTIFIER PRIMARY KEY,
    [order] INT NULL,
    [title] NVARCHAR(200) NOT NULL,
    [url] NVARCHAR(200) NOT NULL,
    [completed] BIT NOT NULL
);
```

In the query and run it to save the table named `dbo.ToDo` by running it.

In Networking blade under the Security section in the SQL server resource, click **Allow Azure services and resources to access this server** under Exceptions.

Go to the Connection strings blade under Setting section in the SQL database resource and copy the connection string under **ADO.NET** (SQL authentication) and store it in some document.

#### Update your function app settings

In the document, replace the value of the `Password` with the password when making the SQL Server and copy the entire string from the document. 

Press F1 and run `Azure Functions: Add New Setting...` and fill out the following prompts: 

- **name**: SqlConnectionString
- **value for "SqlConnectionString"**: (connection string)

After that press F1 again and run `Azure Functions: Download Remote Settings...` and select **Yes to all** to overwrite the existing local settings.

#### Running your function

Just like in the blob storage binding function, press F5 and right click `HttpTrigger1` function under the `Local Project` section and click `Execute Function Now...`. Then enter the request body by Press `Enter` to send the request message in the function.

Go to the **Query editor** blade in the database resource in Azure Portal and log in. Then select **Select Top 1000 Rows** after right click the dbo.ToDo table and check the results if there is an updated row. 

#### Run again and check if the app is updated

Press F1 again to open the command palette and run `Azure Functions: Deploy to function app...`. Choose the function app you made and later select **Deploy** when you are in the redeploying process.

After redeploying, run the `Execute Function Now...` command to run the function.

Check Azure Storage Explorer to see if there is a new message in the queue. After that you successful run the app.

## Clean up the resources

After you finish a function application, go to the resource groups in Azure Portal and delete each one of them to prevent additional costs.

## Link for demo

(running queue message)[https://www.youtube.com/watch?v=dRtpUOPEq0A]

