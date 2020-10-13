# Securing AWS API Gateway with Lambda authorisers

API Gateway is AWS' offering for managing APIs.  The vast majority of APIs are public; however, sometimes you may want to set up internal APIs that are only accessible by employees or clients.  Today, we're going to use a Lambda function to manage authentication and authorisation for an API gateway, which will allow us to set up a secure API suitable for internal use.

At the end of the workshop, we'll have an API Gateway backed by a Lambda authoriser, which uses a Cognito user pool to verify users' identity as part of queries to the API.

- [1: Set up API Gateway](step1/README.md)
- [2: Create Cognito user pool and provision a user](instructions/step2.md)
- [3: Build and deploy Lambda authoriser](instructions/step3.md)
- [Extension: Lambda authorisers using SAML and OAuth 2](instructions/advanced.md)
- [Cleanup](instructions/cleanup.md)
