# Step 1: Set up API Gateway

Today, we'll be looking at a case study based around the company ProductCorp.  ProductCorp is going through a period of rapid expansion, and they've decided to set up a secure API so that their support staff can access basic information easily.  To begin with, we'll set up the API Gateway with a GET route to fetch client data.

## Setting up a Cloud9 environment

It is highly recommended to provision a Cloud9 environment for this lab, as Cloud9 comes with all of the tools we need already installed.  Follow the [instructions provided by AWS](https://docs.aws.amazon.com/cloud9/latest/user-guide/tutorial.html) to do this.

## Checking out the workshop code

Load up the Cloud9 environment that you just provisioned.  In the terminal window at the bottom, run the following command:

```bash
git clone git@github.com:lisushka/secure-api-gateway
```

You should now see the files in this repository in the sidebar of your Cloud9 IDE.

## Deploying the API Gateway

### Creating an IAM user and access key pair

1. In the AWS console, go to `IAM` > `Users`, and click `Add user`.

1. Under `Access type`, select `Programmatic access`.  Go to the next step, and select `Attach existing policies directly`. Attach the `AdministratorAccess` policy, and then click through to review and create the user.  An access key pair will be displayed on screen - we'll need this to configure the CLI profile.

### Configuring the AWS CLI profile

1. In the Cloud9 terminal, run `aws configure`.

1. For `AWS Access Key ID`, copy the access key ID from the IAM console (this always begins with the letters `AK`).

1. For `AWS Secret Access Key`, copy the secret access key from the IAM console (you may have to unhide it).

1. For the `Default region name`, use `us-east-1`.  Leave the default output format blank.

### Deploying CloudFormation

Once the AWS CLI is configured in Cloud9, we can deploy the template using the following commands:

```bash
secure-api-gateway $ aws cloudformation deploy --stack-name secure-api-stack --template-file step1/cf.yaml --capabilities CAPABILITY_IAM
```

## Testing the API Gateway

You can test the API Gateway using the Postman application, if you have it installed.  Otherwise, you can hit the API endpoint using cURL

### Using cURL

1. In the AWS console, open the API gateway landing page.  Click on the `ProductCorp_SupportApi`.

1. In the sidebar, click on `Stages`, and then open the `prod` stage.  At the top of the console page, there will be a blue bar with an Invoke URL.  Copy this URL - we'll need it in the next step.

1. Run the following command in the Cloud9 terminal:

    ```bash
    curl https://<your-api-url>/test
    ```

    You should receive a response that reads "Welcome to the ProductCorp Support API!"

### Using Postman

1. In the AWS console, open the API gateway landing page.  Click on the `ProductCorp_SupportApi`.

1. In the sidebar, click on `Stages`, and then open the `prod` stage.  At the top of the console page, there will be a blue bar with an Invoke URL.  Copy this URL - we'll need it in the next step.

1. Enter your Invoke URL in the Postman address bar, with `/test` appended.

1. Change the HTTP request method to `GET`.

1. Click the `Send` button.  You should receive a response that reads "Welcome to the ProductCorp Support API!"

[Back to home](../README.md)