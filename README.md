# Contacts by XPhone Insights

This repository provides sample Insights integrations for Contacts by XPhone.

## General overview

The Insights feature allows displaying additional contact-related information in a customizable way.
If enabled and the web page URL is provided, it will be displayed in the contact card as an iframe.
The web page will receive contact data and can display it in any way according to your needs, or execute actions.

## Typical workflow

### 1. Decide on the information you want to display

This depends on the data sources and mappings configured in your VDir instance.
For example, if the contact comes from a CRM-based data source and has CRM Record ID as `Custom1` and CRM Endpoint as `Custom2`, these fields can be used to display a clickable link to the CRM page for this contact.

### 2. Create the web page

Implement the web page to display the data according to your design preferences.
Any backend and frontend technologies are supported: from a single HTML page with vanilla Javascript to Angular, React, Vue, or any frontend or backend framework which suits your needs best.

An AI assistant such as Claude Code, ChatGPT or Gemini can do it easily by looking at the examples and docs.

To receive contact info the page needs to accept a `message` event from the parent browser window.
Invoking an action requires sending a message back.
For more information about event names and message formats, see the Contacts By XPhone documentation or `sdk.md` file in the `docs` folder.

### 3. Host the web page

Any web hosting will work, as long as it provides a public HTTPS URL.
For an example on how to host it with Azure Static Web Pages, see the `hosting-azure-static-web-apps.md` file in the `docs` folder.

### 4. Enable Insights

Enable the Insights feature in your Contacts by XPhone Admin Portal, which is accessible from the VDir Admin Panel.
Provide the URL for the hosted page and see the preview with sample data to ensure it looks and works as expected.
If everything is correct, press "Save" to activate the feature for all users in your tenant.