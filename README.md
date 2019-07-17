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

You can use the javascript file to discover the algorithm if you wish to implement it in another language.

### Call a web service

GET: 1 hash per request
POST: 100 or fewer hashes per request -> json[]

Postman config
Swagger config

#### GET

https://civintel.appspot.com/api/voter/verify?hash=${hash}


#### POST
https://civintel.appspot.com/api/voter/verifyList

Content-Type: application/json

Body:

