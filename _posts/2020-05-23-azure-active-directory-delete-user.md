---
layout: post
title: Delete User in Azure Active Directory
subtitle :
tags: [Azure]
author: Bon
comments : True
---

Are you stuck with knowing how to delete a user in Azure Active Directory? Then this quick workaround might help you.

<br>

The assumption here is that you were able to build your CRUD methods now using Graph API and just couldn't delete a user in the directory. Even if you use Postman, it wouldn't just push through. Don't fret, here's how you do it.

<br>

In your tenant:
- Go to Azure Active Directory > Roles and administrators > Global Administrator
- Click Add Assignments > paste the Application ID of your Registered App > click Add

<img src="/assets/img/delete-user.JPG" alt="AZ 900">

<br>

Test your method now by deleting a user! Hope that helps :)

