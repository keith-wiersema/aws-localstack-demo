# aws-localstack-demo

Demo for running a lambda using localstack and the aws cli

Step 1
Create role with Mock IAM
```
aws --endpoint-url=http://localhost:4593 iam create-role --role-name lambda-ex --assume-role-policy-document file://trust-policy.json
```

Step 2
Create function with Mock Lambda
```
aws --endpoint-url=http://localhost:4574 lambda create-function --function-name hello-function --zip-file fileb://function.zip --handler hello.handler --runtime nodejs12.x --role arn:aws:iam::000000000000:role/lambda-ex
```

Step 3
Execute function with Mock Lambda
```
aws lambda --endpoint-url=http://localhost:4574 invoke --function-name hello-function --payload '{"name": "lambda"}' out
cat out
```
