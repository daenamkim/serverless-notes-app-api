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
