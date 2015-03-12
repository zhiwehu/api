# Errors

The Quadrant API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid
401 | Unauthorized -- Your API key is wrong
403 | Forbidden -- The info requested is hidden for administrators only
404 | Not Found -- The specified info could not be found
405 | Method Not Allowed -- You tried to access info an invalid method
406 | Not Acceptable -- You requested an invalid format
410 | Gone -- The info requested has been removed from our servers
418 | It's a great day for economics
429 | Too Many Requests -- You're requesting too much data! Slown down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
