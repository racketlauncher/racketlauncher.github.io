---
layout: post
title: Establish Workday API connection using Postman and SoapUI
subtitle :
tags: [Workday]
author: Bon
comments : True
---

For this post, I will be sharing with you how I was able to establish connection with Workday API using Postman and SoapUI.

<br>

So, the plan here is that you are going to send requests externally to Workday using their public API. I am posting this because I had a hard time before making this one work due to the fact that the documentation for this is quite limited.

<br>

Pre-requisite:
- A Workday account. To know more about Workday, you may go to https://workday.com/. 
- Your tenant's API endpoint and credentials.
- Download the WSDL file from their [service directory](https://community.workday.com/sites/default/files/file-hosting/productionapi/versions/v34.0/index.html).
- From WSDL file, get the sample SOAP body request of the service you want to use. You may remove non-required fields in the XML.

<br>

Establishing connection using Postman:
- The format for the API endpoint is https://{Subdomain}.workday.com/ccx/service/{Your Tenant}/{Service Name}.
- Include your credentials in your body request - username and password. 
- The username's format is {Your username}@{Your tenant}.
- Hit the send button and you will be able to get the requested data.

<img src="/assets/img/workday_functions.JPG" alt="Postman">

<br>

Establishing connection using SoapUI:
- Import the WSDL file.
- Expand the project and choose the service you want to send request.
- Double click the sample Request and a pop-up will appear.
- Modify the XML body request, just like what we did in the Postman.
- Don't forget to put your API endpoint in the URL bar above.
- Hit the green button to send the request.
- Your results should appear in the right pannel.

<img src="/assets/img/workday_functions_soap.JPG" alt="SoapUI">

<br>

There you go! You are now able to establish connection to your Workday tenant and you may now integrate the API to your apps. As for me, since this blog is focused on Cloud tech, I will be posting soon on how I was able to integrate the Workday API with Azure Functions.




