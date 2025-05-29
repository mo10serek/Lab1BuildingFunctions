# Lab 1 Building Functions

## Links to other repositories 

[Blob storage binding tutorial](https://github.com/mo10serek/Blob-Storage-Binding-Tutorial)

[SQL Database binding tutorial](https://github.com/mo10serek/SQL-Database-Binding-Tutorial)

## Sign in to Azure

before you run the functions in the links above, you need to sign in to Azure. To do that, install the Azure exetenston and click **Sign in to Azure** in the **Azure Resources** under **Resources**.

## Creating a Azure Function for each resoruce

### Binding Blob Storage

Before you start running, you need to make a function app for each binding application. Press F1 to open the command palette and select **Azure Functions: Create Function App in Azure** and then fill out the following detail:

Subscription: the subscription you usally you use
name: blobstoragebunding or sqldatabasebinding
Location: East US
runtime stack: newest python version (Python 3.12)

Wait until each of the individual resoruces had been created that are displayed in AZURE: ACTIVITY LOG

After that it will show you all of the resources created. Start running the functions 

#### Run blob storage binding function

In order to run the blob storage binding function. First you need to start the function app by pressing F5 and right click `HttpExample` function under the `Local Project` section and click `Execute Function Now...`. Then enter the request body by Press `Enter` to send the request message in the function.

#### Connect Storage Explorer

Download `Microsoft Azure Storage Explore` in this link: https://storageexplorer.com/.

After downloading, open the application and click the person icon and click the Sign in with Azure... link. 

In the **Connect** window pick **Add an Azure account** and have your Azure environment your enviroment and then sign in. 

Then pick your subscription and select **Open Explorer**

#### Check the Output queue

Go to Visual Studio Code and press F1 to open the command palette and run `Azure Storage: Open in Storage Explorer` and pick your storage account.

If you do that, then it will open your storage account in Azure Storage Explorer. Then open the Queues node and open **outqueue** queue. After that, you will see one message which is "Azure". 

#### Run again and check if the app is updated

Press F1 again to open the command palette and run `Azure Functions: Deploy to function app...`. Choose the function app you made and later select **Deploy** when you are in the redeploying process.

After redeploying, run the `Execute Function Now...` command to run the function.

Check Azure Storage Explorer to see if there is a new message in the queue. After that you successful run the app.

### Binding SQL Queue



