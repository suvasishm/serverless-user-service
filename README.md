This serverless service is aimed at creating user and authentication.

To do so I used the previously created template as follows:

```$ git clone https://github.com/suvasishm/serverless-project-template.git```

##### Made a copy of the template project
```$ cp -R serverless-project-template serverless-user-service```\
```$ cd serverless-user-service```

##### removed existing git repo info
```$ rm -rf .git```

##### created a function
```$ serverless create function -f createUser --handler src/functions/createUser.createUser --path src/tests```

##### tested the new function
```$ mocha src/tests/createUser.js```

Opened serverless.yml; updated service name, functions etc as it is now; made other required changes

##### associating the service with the serverless account
```$ serverless```

##### deploy
```$ sls deploy```

Log:
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
  POST - https://<app_id>.execute-api.us-east-1.amazonaws.com/dev/v1/user
functions:
  createUser: serverless-user-service-dev-createUser
layers:
  None
Serverless: Publishing service to the Serverless Dashboard...
Serverless: Successfully published your service to the Serverless Dashboard: https://dashboard.serverless.com/tenants/xxxxx/applications/user-service-app/services/serverless-user-service/stage/dev/region/us-east-1
````

##### call create user api
```$ curl --request POST     --url https://<app_id>.execute-api.us-east-1.amazonaws.com/dev/v1/user         --data '{"username":"suvasish", "password":"password"}' -H 'Content-type: application/json' -i```

##### call login api
```$ curl --request POST     --url https://<api_id>.execute-api.us-east-1.amazonaws.com/dev/v1/user/login   --data '{"username":"suvasish", "password":"password"}' -H 'Content-type: application/json' -i```

##### clear the stack
```$ sls remove```

#### Prerequisites:
```$ npm install --save jsonwebtoken```\
```$ npm install --save bcryptjs```\
```**Add a param called 'JWT_SECRET' in your serverless deployment profile```


Ref: https://www.serverless.com/learn/tutorial/user-creation/