# Step 1: Set up API Gateway

Today, we'll be looking at a case study based around the company ProductCorp.  ProductCorp is going through a period of rapid expansion, and they've decided to set up a secure API so that their support staff can access basic information easily.  To begin with, we'll set up the API Gateway with a GET route to fetch client data.

## Setting up a Cloud9 environment

It is highly recommended to provision a Cloud9 environment for this lab, as Cloud9 comes with all of the tools we need already installed.  Follow the [instructions provided by AWS](https://docs.aws.amazon.com/cloud9/latest/user-guide/tutorial.html) to do this.

## Checking out the workshop code

1. Load up the Cloud9 environment that you just provisioned.  In the terminal window at the bottom, run the following command:

    ```bash
    git clone git@github.com:lisushka/secure-api-gateway
    ```

1. You should now see 

## Deploying the API Gateway template

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