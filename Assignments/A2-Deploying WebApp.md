# Deploying a Python (Django) web app with PostgresSQL in Azure
In this assignment we'll be deploying a web app with a PostGresSQL database to Azure. We'll be using the Django web framework and the Azure Database for PostgreSQL service.

For this assignment, you will first work through the following tutorial to deploy a Django web app to Azure:
- [Tutorial: Deploy a Django web app with PostgreSQL in Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/tutorial-python-postgresql-app?tabs=django%2Cwindows&pivots=azure-portal)

This tutorial will guide you through the process of deploying a Django web app to Azure App Service and connecting it to an Azure Database for PostgreSQL.  Once you have completed the tutorial, you will use the following repository [https://github.com/ISYS53403/restaurantweb-azure-appservice](https://github.com/ISYS53403/restaurantweb-azure-appservice) to deploy the Restaurant Web application to Azure App Services.

*Be sure to fork this repository to your own GitHub account and then use your own repository to deploy the app to Azure.  This will allow you to see how automated changes are pushed to the app services code when changes are made to the code base.*

Please begin directly from **Step 1** of the tutorial, applying the following changes and additions as you proceed.  The instructions prior to Step 1 are for running the app locally.  You are welcome to do so in order to test the application, but it is not required.

## Before you begin
You will need to have `git` installed on your local machine.  You can download it from [https://git-scm.com/downloads](https://git-scm.com/downloads).  

You will also need to have an Azure account.  If you do not have one, you can sign up for a free account at [https://azure.microsoft.com/en-us/free/](https://azure.microsoft.com/en-us/free/).

## Deliverables
1. A screenshot of the webpage running, be sure to include the URL in the screenshot.
2. A screenshot of the Resource Visualizer showing the resource group and the resources created by the deployment.
3. Answer the questions in the assignment on the submission screen.

## Changes and Additions
Keep in mind the following steps as you proceed through the tutorial:

**Before you begin**: The very first step is to fork the repository [https://github.com/ISYS53333/restaurantweb-azure-appservice]. When we see to 'Fork' a repository we are telling you to make a copy ofthe repository into your own account. Forking a repository allows you to freely experiment with changes without affecting the original project.  You can fork the repository by clicking the "Fork" button in the upper-right corner of the repository page.

There are several locations in the tutorial where you will be told to check a particular box or select a particular service.  You will be asked about a few of these decisions in the assignment questions, so be sure to take note of the choices you make and research why you are being asked to select the default or a different option.

### Stage 1 - Create App Service and PostgreSQL database
- You will need to clone the repository you forked to your local machine. The instructions are provided in the tutorial, but you will need to use the URL of your forked repository.  This will be the name of the repository in your account with a .git extension.  For example, when I forked this repository it created a repository in my account called `restaurantweb-azure-appservice` and the URL is `https://github.com/MLDERES/restaurantweb-azure-appservice.git`
- A common pattern is to name your resource group something descriptive of the resources it will contain.  For example, you could name your resource group `restaurantweb-rg`. (Note the -rg suffix is a common pattern for resource groups, but not required.)
- When providing a name for your app service, you should use a name that is unique to Azure.  You can use your name or some other unique identifier to ensure it is globally unique (that is, no one else in the world has ever named their app).  For example, you could use `restaurantweb-mlderes` as the name of your app service.

### Stage 2 - Verify connection settings
- NOTE: As of this writing `Application Settings` referred in the tutorial have moved and are now in the `Environment Variables` section of the Configuration blade.  Wherever you see `Application Settings` in the tutorial, you should look for `Environment Variables` instead.
- This is a good point to take a screenshot of the Resource Visualizer.  You can access the Resource Visualizer by clicking on the "Resource Visualizer" link in the left-hand menu of the Azure Portal.  This will show you all the resources in your resource group and how they are connected.

### Stage 3 - Deploy sample code
- If you have already forked this repository, then you can skip the step to clone the repository.
- Again, in step 3 of the tutorial it uses the term `app settings` you should read as `environment variables`.
- When asked to `Configure Authentication`: Choose **Basic Authentication** instead of User-Assigned Identity under Authentication Types.

### Stage 4 - Generate the database schema
- The first time you SSH into your app service it may take 60-90 seconds to connect.  Be patient and try again if it fails the first time.
- After completing the two steps in stage 4 of the tutorial, you will need to execute an additional command to populate the database with initial data:

  ```bash
  python manage.py loaddata menu_data.json
  ```

### Stage 5 - Browse to the web app
- You will need to take a screenshot of the webpage running.  Be sure to include the URL in the screenshot.

### Stage 6 - Stream Diagnostics Logs
- There is nothing to do here if you already completed this in the tutorial.
- What you might do at this point is to make a change to the web application and push the change to your forked repository.  This will trigger a deployment of the new code to your app service.  You can then check the logs to see the deployment process in action. For instance, look for line which describes the restaurant in the `restaurant/templatesa/restaurant/home.html` file and change it to something else.  Then commit and push the change to your forked repository.  You can then check the logs to see the automatic deployment process in action.

### Stage 7 - Clean up resources
- Make sure to take a screenshot of your web page running and the resource visualizer before you delete the resources.
