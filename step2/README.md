# Step 2: Create Cognito user pool and provision a user

Now that we've created ProductCorp's API Gateway, we need a method of authenticating company staff to use the API.  In order to do this, we're going to create an Amazon Cognito user pool, and then provision users for the sales staff.

##  Setting up Cognito user pool

Setting up the Cognito user pools requires us to deploy the new CloudFormation template with the user pools attached:

```bash
secure-api-gateway $ aws cloudformation deploy --stack-name secure-api-stack --template-file step2/cf.yaml --capabilities CAPABILITY_IAM
```

This will add the Cognito user pools to our CloudFormation stack.

## Creating Cognito users

1. In the AWS console, open the Cognito landing page.  Click on the `ProductCorp_SupportPool`.

1. In the sidebar, click on `Users and Groups`.  At the moment, we have no users in our pool.  Click on `Create user` to add one.

1. Enter your email address in both the `Username` and `Email` fields.  Create a temporary password - you'll be prompted to change it later.  You will use your email as the username, and your temporary password to sign in.

1. Click the `Create user` button to add yourself to the user pool.