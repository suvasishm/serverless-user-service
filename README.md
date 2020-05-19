This test serverless service is aimed at creating user and authentication.

To do so I used the previously created template as follows:

```$ git clone https://github.com/suvasishm/serverless-project-template.git```

##### made a copy of the template project

```$ cp -R serverless-project-template serverless-user-service```

```$ cd serverless-user-service```

##### removed existing git repo info

```$ rm -rf .git```

##### created a function

```$ serverless create function -f createUser --handler src/functions/createUser.createUser --path src/tests```

##### tested the new function

```$ mocha src/tests/createUser.js```

Opened serverless.yml; updated service name, functions etc as it is now; make other required changes

##### associating the service with the serverless account

```$ serverless```

##### deploy

```$ sls deploy```

```
Serverless: Stack update finished...
Service Information
service: serverless-user-service
stage: dev
region: us-east-1
stack: serverless-user-service-dev
resources: 23
api keys:
  None
endpoints:
  POST - https://xxxxx.execute-api.us-east-1.amazonaws.com/dev/v1/user
functions:
  createUser: serverless-user-service-dev-createUser
layers:
  None
Serverless: Publishing service to the Serverless Dashboard...
Serverless: Successfully published your service to the Serverless Dashboard: https://dashboard.serverless.com/tenants/xxxxx/applications/user-service-app/services/serverless-user-service/stage/dev/region/us-east-1
````

##### call the api

```$ curl --request POST --url https://xxxx.execute-api.us-east-1.amazonaws.com/dev/v1/user --data '{"username":"suvasish", "password":"password"}' -H 'Content-type: application/json' -i```

Response
```
HTTP/2 201 
content-type: application/json
....
```