# Step 3: Build and deploy Lambda authoriser

With the Cognito pool deployed, and a new user created, we can now set up an authoriser which uses our user pool to authenticate any requests to the API.

## Connecting API Gateway to Cognito user pool authoriser

In order to connect everything up, we need to deploy the new CloudFormation template with the user pools attached:

```bash
secure-api-gateway $ aws cloudformation deploy --stack-name secure-api-stack --template-file step3/cf.yaml --capabilities CAPABILITY_IAM
```

Our CloudFormation stack now includes an API authoriser that queries the Cognito user pool every time a request is made to the API Gateway.

## Pulling it all together

1. In the AWS console, open the API Gateway landing page. Go to the `ProductCorp_SupportAPI`.

1. Go to the `Stages` tab, and verify that the `prod` stage is still deployed.

1. In the sidebar, click on `Users and Groups`.  At the moment, we have no users in our pool.  Click on `Create user` to add one.

1. Enter your email address in both the `Username` and `Email` fields.  Create a temporary password - you'll be prompted to change it later.  You will use your email as the username, and your temporary password to sign in.

1. Test the API Gateway using the instructions in Step 1.  You should receive a failure response, as we're not passing a valid token.  We'll cover token handling in the Extension section.