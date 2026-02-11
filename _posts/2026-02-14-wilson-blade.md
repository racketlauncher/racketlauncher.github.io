---
layout: post
title: Retrieving Azure B2C claims for Sitecore via AD Graph API
subtitle :
tags: [Azure, Sitecore]
author: Bon
comments : True
---

Let's go and start fresh with some Azure action! So I've been trying to play around with the AD Graph API to integrate it with Sitecore.

<br>

In this post, I'll be tackling how to retrieve Azure B2C claims from Sitecore via AD Graph API. Claims are needed to get the access token from Azure in order to retrieve data such as the user details. Reading through the [Graph API documentation](https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-reference-tokens#claims-in-id-and-access-tokens), it seems like it is a walk in the park. But it isn't the case when it comes to Sitecore. 

<br>

At first, I had been trying to retrieve the user details from my registered application in the Azure tenant but I failed to do so. You see, Sitecore overrides the claims that I am requesting. This is because the Sitecore security model somehow replaces them as mentioned from this [post](http://blog.baslijten.com/how-to-add-federated-authentication-with-sitecore-and-owin/). In order to retrieve the claims, you have to access the cookies from the http request.

<br>
{% highlight python %}
var cookie = httpRequest.Cookies[".AspNet.Cookies"];
var secureDataFormat = new TicketDataFormat(new MachineKeyProtector());
return secureDataFormat.Unprotect(cookie.Value);
{% endhighlight %}

<br>
In the code, the cookie type .AspNet.Cookies is accessed and have the authentication ticket decrypted after, as it is encrypted by default.
<br>

<br>

{% highlight python %}
var authenticationTicket = GetAuthenticationKeyTicket(httpRequest).Identity;
return authenticationTicket.Claims.Where(claim => claim.Type.Equals(claimType)).FirstOrDefault().Value;
{% endhighlight %}

<br>

In my utility class for the claims, I accessed the cookies and retrieved the [claim type](https://docs.microsoft.com/bs-latn-ba/azure/architecture/multitenant-identity/claims) that I needed.

<br>

Now that we have the claims challenge all sorted out, we are now ready to do some Graph API request manipulation with Sitecore. I'll be discussing this on my next post. Kbye lol

