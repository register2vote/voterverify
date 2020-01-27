# Voter Registration Verification

This tool is intended to automate checking voter registration.  You can find out if a given voter, or list of voters, is registered.

Overall, the process looks like this:

* Get a cryptographic key (one time)
* Generate a hash for each voter in your verification list
* Call a web service method, providing your hashes
* Read the responses

### Get a key

Before you can use our endpoint, you'll need credentials.  Request a key by emailing:

help@register2vote.org

### Generate a hash

Generate a hash for each voter.  A hash contains no voter personal information, so submitting them to us does not disclose sensitive data.

We have a javascript file that you can use to generate hashes...

  <<makeHash.js>>

You can use the javascript file to discover the algorithm if you wish to implement it in another language.

### Call a web service

GET: 1 hash per request
POST: 100 or fewer hashes per request -> json[]

For Postman users:

  <<Postman config>>

#### GET

https://civintel-endpoints-4r6lbwbrta-uc.a.run.app/api/voter/verify?key=${key}&hash=${hash}


#### POST
https://civintel-endpoints-4r6lbwbrta-uc.a.run.app/api/voter/verifyList?key=${key}

Content-Type: application/json

The "confidence score" returned by VoterVerify is the number of hashes which match a submission.  Current possible values are 0-3.  A "hash" in the case of VoterVerify is a particular combination of voter attributes like last name, zip code, date of birth, etc.  We generally consider a confidence score above 0 as success/verified because it is likely that some hashes may not match due to missing or inconsistent value in either the input/submitted fields or the stored/voterfile fields.

### POWER USERS

After authenticating with your Google Cloud account, access the API documentation:

https://endpointsportal.civintel.cloud.goog
