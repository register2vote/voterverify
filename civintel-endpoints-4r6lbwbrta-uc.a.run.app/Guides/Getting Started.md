# Getting Started
---

# Voter Registration Verification

This tool is intended to automate checking voter registration.  You can find out if a given voter, or list of voters, is registered.

Overall, the process looks like this:

* Get a cryptographic key (one time)
* Generate a hash for each voter in your verification list
* Call a web service method, providing your hashes
* Read the responses

### The API key

You should have received an API key when you were granted access to this API interface. Please use this key to access the API.

### Enable the API

You can also make calls to this API by enabling it in a Cloud Platform project.
1. [View this API](https://console.developers.google.com/apis/api/{{apiHost}}/overview) in the Google APIs Console.
2. Click the **Enable** button, then wait for it to complete.
3. You can now call the API using the API key you created!

### Using the API

Browse the reference section of this site to see examples of what you can do with this API and how to use it. 

You can use the **Try this API** tool on the right side of an API method page to generate a sample request.

### Generate a hash

Generate a hash for each voter.  A hash contains no voter personal information, so submitting them to us does not disclose sensitive data.

We have a javascript file that you can use to generate hashes. It's located at:

https://github.com/register2vote/voterverify

You can use the javascript file to discover the algorithm if you wish to implement it in another language.

### Call a web service

GET: 1 hash per request
POST: 100 or fewer hashes per request -> json[]

For Postman users:

#### GET

https://civintel-endpoints-4r6lbwbrta-uc.a.run.app/api/voter/verify?key=${key}&hash=${hash}


#### POST
https://civintel-endpoints-4r6lbwbrta-uc.a.run.app/api/voter/verifyList?key=${key}

Content-Type: application/json

Body:


### POWER USERS

After authenticating with your Google Cloud account, access the API documentation:

https://endpointsportal.civintel.cloud.goog
