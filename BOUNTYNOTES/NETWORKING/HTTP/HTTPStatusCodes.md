# HTTP Status Codes

## Status Code Ranges

| Range | Category | Description |
|---|---|---|
| 100-199 | Informational Response | The first part of the request has been accepted and the client should continue sending the rest of the request. These codes are no longer very common. |
| 200-299 | Success | The request was completed successfully. |
| 300-399 | Redirection | The client is redirected to another resource, webpage, or website. |
| 400-499 | Client Errors | There was an error with the client's request. |
| 500-599 | Server Errors | An error occurred on the server side, often indicating a problem handling the request. |

## Common HTTP Status Codes

| Status Code | Name | Description |
|---|---|---|
| 200 | OK | The request was completed successfully. |
| 201 | Created | A resource has been created, such as a new user or blog post. |
| 301 | Moved Permanently | Redirects the client to a new webpage or tells search engines that the page has permanently moved. |
| 302 | Found | A temporary redirect to another resource. |
| 400 | Bad Request | Something was wrong with or missing from the client's request, such as a required parameter. |
| 401 | Not Authorised | The client must authenticate before accessing the resource, commonly with a username and password. |
| 403 | Forbidden | The client does not have permission to view the resource, whether logged in or not. |
| 404 | Page Not Found | The requested page or resource does not exist. |
| 405 | Method Not Allowed | The requested HTTP method is not allowed for the resource, such as sending GET when POST is required. |
| 500 | Internal Server Error | The server encountered an unexpected error while handling the request. |
| 503 | Service Unavailable | The server cannot currently handle the request, often because it is overloaded or undergoing maintenance. |
