# Introduction

Welcome to the SalesSeek API! You can use our API to access all our API endpoints, such as the [Deal API](https://github.com/tripit/slate) to look up deal values, or the [Individual API](https://github.com/tripit/slate) to look up email addresses. 

The API is organized around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer). All requests should be made over SSL. All request and response bodies, including errors, are encoded in JSON.

URIs for SalesSeek's REST API resource have the following structure:

`https://{CLIENT_ID}.salesseek.net/api/{RESOURCE}?{KEY1}={VALUE1}&{KEY2}={VALUE2}`

Variable |  Description
--------- | ------- 
CLIENT_ID | The unique ID for your SalesSeek account. You can find this as the sub-domain when accessing your account. 
RESOURCE | Specific [resource]() type  to be requested.
KEYx | Parameter identifier matching one resource's parameter (optional)
VALUEx | Value asociated to KEYx