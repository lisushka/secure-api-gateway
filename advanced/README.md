# Extension: Lambda authorisers using SAML and OAuth 2

As the basic example that we just went through shows, authorising requests to API Gateway through Cognito user pools is a very simple process.  However, more mature organisations may wish to secure their internal APIs using existing single sign-on solutions (ADFS, AzureAD, Okta, etc).  Using Lambda authorisers, API Gateway can authenticate and authorise users through most common SSO providers.

[This example](https://github.com/mcguinness/node-lambda-oauth2-jwt-authorizer) by Karl McGuinness provides an overview of configuring your API Gateway to use OAuth 2 tokens through a Lambda authoriser.  This Lambda function can be zipped up and plugged directly into the CloudFormation template from this lab instead of the Cognito user pools.  Replace the `UserPoolAuthoriser` in the template with the following piece of code to get it working:

```yml
APILambdaAuthoriser:
Type: AWS::ApiGateway::Authorizer
Properties:
    IdentitySource: method.request.header.Authorization
    AuthorizerUri: !Join
    - ""
    - - "arn:aws:apigateway:"
        - !Ref "AWS::Region"
        - ":lambda:path/2015-03-31/functions/"
        - !GetAtt
        - <ID of lambda auth function in template>
        - Arn
        - /invocations
    Name: ApiAuthoriser
    RestApiId: !Ref InternalSupportAPI
    Type: TOKEN
```

AWS also provides [several custom authorisers](https://github.com/awslabs/aws-apigateway-lambda-authorizer-blueprints) that you can edit to suit your use-case.

[Back to home](../README.md)