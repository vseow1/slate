# Errors

The Spacio API uses the following error codes:


Error Code | Meaning
---------- | -------
access-denied | Insufficient privileges for specified resource
invalid-bid | The utilized Brokerage ID does not exist
invalid-email | No user found (It's recommended that you redirect the user to `redirectUrl` if you receive this error)
invalid-sid | No Spacio ID found
invalid-ukey | UKEY not found
no-results | No registrants found
not-authorized | API key is not authorized
rate-reached | API rate limit reached (Next reset at: 2017-01-01 0:00:00 UTC)
