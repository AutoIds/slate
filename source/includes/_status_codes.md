# Status Codes


The AutoID API returns the following status codes:


Code | Meaning
---------- | -------
200 | OK. Successful request.
400 | Bad Request  Returns JSON with the error message.
401 | Unauthorizedd. Your API key is wrong or not allowed access to resource.
403 | Forbidden. The resource requested is hidden for administrators only.
404 | Not Found. The specfied resource could not be found.
405 | Method Not Allowed. You tried to access a resource with an invalid method.
406 | Not  acceptable. You requested a format that isn't json.
410 | Gone. The resource requested has been removed from our servers.
422 | Unprocessable Entity. Your request is missing arguments.
500 | Internal Server Error We had a problem with our server. Try again later.
503 | Service Unavailable We're temporarily offline for maintenance. Please try again later.
