# AzFun

This repo contains material alongside of my session at Collabsummit 2021. I already [blogged about the solution on m365princess.com](https://www.m365princess.com/blogs/putting-fun-azure-functions-managed-identity-microsoft-graph/). Find the slides of my session on the `media` folder.

## Azure Function

and other resources are deployed with a script, which but you can find in the `src` folder.

## Custom connector

To create the custom connector, obtain

- the Function app URL
- the app key

from the Azure portal. Then

- Open [make.powerapps.com](https://make.powerapps.com/)
- Select **Data**
- Select **Custom Connecors**
- Select **New Connector**
- Type in `<your-functionapp-name>.azurewebsites.net` as **Host**
- Select **Security**

Then,

- Select `API Key` as **Authentication type**
- Type in something like `API Key` for **Parameter Label**
- Type in something like `code` for **Parameter name**
- Select `Query` as **Parameter location**
- Select **Definition**

Then,

- Select **New action**
- Type in something like `GetGroups` for **Summary**, **Description**, and **Operation ID**
- For **Request**, select **Import from sample**
- Select **Get**
- Type in the URL of the Function like `https://<your-functionapp-name>.azurewebsites.net/api/<your-function>`
- For **Response**, select **Add a default response**
- Type in the header `content-type application/json`
- In the body provide the response of the request you sent. You can either obtain this from the Azure portal when you select your function and select **Test + Run** or you can obtain it from [Graph Explorer](https://aka.ms/ge) when you ran the Get groups sample.
- Select **Import**

Now,

- Select **Create Connector**
- Select **New connection** and provide the App key as API key
- Select **Test operation** to test your connector.

It can now be used in Power Apps and Power Automate.

If you have any questions, please [reach out to me on twitter](https://twitter.com/LuiseFreese) 💖