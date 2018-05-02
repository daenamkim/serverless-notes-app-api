# Serverless Notes App API

Based on awesome [serverless-stack](https://serverless-stack.com/) I built API codes.

There is a problem after deployment.

> AWS > IAM > Roles > ...-labmdaRole menu > Permissions tab > **Edit ...-lambda policy** > Add as below.

```json
{
  "Effect": "Allow",
  "Action": [
    "dynamodb:DescribeTable",
    "dynamodb:Query",
    "dynamodb:Scan",
    "dynamodb:GetItem",
    "dynamodb:PutItem",
    "dynamodb:UpdateItem",
    "dynamodb:DeleteItem"
  ],
  "Resource": "arn:aws:dynamodb:us-east-1:*:*"
}
```

[GitHub Issue](https://github.com/AnomalyInnovations/serverless-stack-com/issues/28)

## API Test

**Add a note**

```sh
apig-test \
--username='daenam.kim@gmail.com' \
--password='Passw0rd!' \
--user-pool-id='us-east-1_6S1G4MTRL' \
--app-client-id='4548c0tvempdaebd5pls26iraq' \
--cognito-region='us-east-1' \
--identity-pool-id='us-east-1:9c336fa2-7aa2-4af8-b1cb-bbf7b75b28be' \
--invoke-url='https://6n5vigj2k0.execute-api.us-east-1.amazonaws.com/prod' \
--api-gateway-region='us-east-1' \
--path-template='/notes' \
--method='POST' \
--body='{"content":"hello world","attachment":"hello.jpg"}'
```

**Add an account into cognitor user pool.**

```sh
aws cognito-idp sign-up \
  --region us-east-1 \
  --client-id 4548c0tvempdaebd5pls26iraq \
  --username daenam.kim@gmail.com \
  --password Passw0rd!
```

**Confirm an account signed up **

```sh
aws cognito-idp admin-confirm-sign-up \
  --region us-east-1 \
  --user-pool-id us-east-1_6S1G4MTRL \
  --username daenam.kim1@gmail.com
```
