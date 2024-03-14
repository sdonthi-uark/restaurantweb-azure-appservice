# Deploying a Python (Django) web app with PostgresSQL in Azure
In this assignment we'll be deploying a web app with a PostGresSQL database to Azure. We'll be using the Django web framework and the Azure Database for PostgreSQL service.

For this assignment, you will first work through the following tutorial to deploy a Django web app to Azure:
- [Tutorial: Deploy a Django web app with PostgreSQL in Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/tutorial-python-postgresql-app?tabs=django%2Cwindows&pivots=azure-portal)

This tutorial will guide you through the process of deploying a Django web app to Azure App Service and connecting it to an Azure Database for PostgreSQL.  Once you have completed the tutorial, you will use the following repository [https://github.com/ISYS53333/restaurantweb-azure-appservice](https://github.com/ISYS53333/restaurantweb-azure-appservice) to deploy the Restaurant Web application to Azure App Services.

*Be sure to fork this repository to your own GitHub account and then use your own repository to deploy the app to Azure.  This will allow you to see how automated changes are pushed to the app services code when changes are made to the code base.*

Please begin directly from **Step 1** of the tutorial, applying the following changes and additions as you proceed.  The instructions prior to Step 1 are for running the app locally.  You are welcome to do so in order to test the application, but it is not required.

## Deliverables
1. A screenshot of the Azure App Service dashboard showing the deployed web app.
2. A screenshot of the webpage running, be sure to include the URL in the screenshot.
3. A screenshot of the Resource Visualizer showing the resource group and the resources created by the deployment.
4. Answer the questions in the assignment on the submission screen.

### Changes and Additions
Keep in mind the following steps as you proceed through the tutorial:

- **Step 4 (Configure Authentication):** Choose **Basic Authentication** instead of User-Assigned Identity under Authentication Types.

- **After completing Step 4:** Execute an additional command to populate the database with initial data:

  ```bash
  python manage.py loaddata menu_data.json
  ```

