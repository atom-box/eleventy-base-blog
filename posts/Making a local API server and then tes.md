---
title:  Start a local Node API server and then test it
description:
date: 2021-09-21
tags:
  - linux
  - troubleshooting
layout: layouts/post.njk
---


## Make the API

1. Make sure Mongo DB is [installed](https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-20-04) and running:
`$ sudo systemctl status mongod`
2. Clone the server from [ makinhs/
rest-api-tutorial](https://github.com/makinhs/rest-api-tutorial).
3.  Install dependencies: `npm install`
4. Start it: `npm start`

The server is now running on http://localhost:3600

## Several ways to hit the server API with a POST

### Using the console in a browser to POST
The console in Firefox or Safari can run JS that will send a post. console may complain "Be careful about pasting in code you find on Internet sites".
```
fetch('http://localhost:3600/users', {
        method: 'POST',
        headers: {
            "Content-type": "application/json"
        },
        body: JSON.stringify({
            "firstName": "Marcos",
            "lastName": "Silva",
            "email": "marcos.henrique@toptal.com",
            "password": "s3cr3tp4sswo4rd"
        })
    })
    .then(function(response) {
        return response.json();
    })
    .then(function(data) {
        console.log('Request succeeded with JSON response', data);
    })
    .catch(function(error) {
        console.log('Request failed', error);
    });
```

### Using cURL at the CLI to POST
In the BASh terminal:
```
curl -d $'{"firstName":"Barry", "lastName":"Gordy", "email": "boss@motown.com", "password": "abc"}' -H "Content-Type: application/json" -X POST http://localhost:3600/users
```

### Using the Insomnia GUI to POST

Download Insomnia API tester. Insomnia is a free application, similar to Postman. Start Insomnia. Once you are in a project, hit Ctl + n to start a new request. The center panel near the top has a one line slot is where you put the request, similar to a web browser's top slot. (You're in the right place if the slot has a SEND button on the right and a dropdown on the left for GET, PUT, et cetera).

Example:
1. Ctl + n
2. In the top slot type __https://httpbin.org/get__
3. Select __GET__.  Press __Send__
4. The server's response data in JSON should appear in the right pane.

Example:
1. Ctl + n
2. In the top slot type: __localhost:3600/users__ (no http://)
3. Select __POST__
4. Add data in the panel directly below the slot:
```
{
    "firstName" : "Barry",
    "lastName" : "Gordy",
    "email" : "barry.gordy@toptal.com",
    "password" : "do-re-mi  "
 }
```
5. Press __SEND__. The response should just be a one line id for the new user created in this case.


### To do next, modify the server

These are left as an exercise to the reader, as they say:

    Implement proper validations (e.g., make sure that user email is unique)
    Implement unit testing and error reporting
    Prevent users from changing their own permission level
    Prevent admins from removing themselves
    Prevent disclosure of sensitive information (e.g., hashed passwords)
    Move the JWT secret from common/config/env.config.js to an off-repo, non-environment-based secret distribution mechanism
    Convert the codebase from its use of JavaScript promises over to the async/await technique.

