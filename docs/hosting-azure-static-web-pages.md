# Hosting in Azure Static Web Apps

This document shows a simple way to host the Insights web page in Azure Static Web Apps.

## Prerequisites

1. Your Insights page is fully client-side (e.g. HTML, JS and CSS) and needs no backend
2. You have an Azure account with admin rights in your tenant
3. You have [NodeJS 20.0+](https://nodejs.org/en/download) and [Azure CLI 2.6+](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) installed

## Creating the resource

To create a new static web app via the command line, follow this guide: [create a static web app on Azure](https://learn.microsoft.com/en-us/azure/static-web-apps/deploy-web-framework?tabs=bash&pivots=vanilla-js#create-a-static-web-app-on-azure).

To create it in the Azure Portal, do the following:

1. Open Azure Portal
2. Search for "Static Web Apps" in the top search bar
3. Click "Create"
4. Select the subscription, hosting plan, provide a meaningful name (e.g. "CbyX Insights").
5. Deployment configuration: select "Deployment token"
6. Skip other steps, press "Create"
7. Find the newly created resource using the search bar and open it
8. *Optional*: configure a custom domain using Settings → Custom Domains.
9. In the Overview tab, click "Manage deployment token" and copy the value.

## Deploying the web page

To deploy the web page using Azure CLI, do the following:

1. Open the console in the folder where your web app is located, e.g. `C:\sources\insights`
2. Run the following command in the console:

    ```powershell
    swa deploy --deployment-token <YOUR TOKEN>
    ```

    Where `<YOUR TOKEN>` is the deployment token copied in step 9 above.
3. Open the website to make sure it's deployed.

*Note*: the page will not be fully functional when simply opened in the browser, because the Contacts by XPhone SDK is only available when loaded in an iframe. To test the website before publishing it to actual users, see the Insights configuration page in you Contacts by XPhone Admin Portal.