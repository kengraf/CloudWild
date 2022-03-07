# CloudWild

### CloudFormation approach
Experiment with CloudFormation and serverless backends

Credit for where I started [template example](https://bl.ocks.org/magnetikonline/c314952045eee8e8375b82bc7ec68e88)  

### Template currently provides:  
-API Gateway to call Lambda via POST.
-Lambda that echos user's IP address.

### Setup
AWS cloudshell
git clone 'repo URL'
  
### CloudFormation
Deploy command will create the following:
AWS::ApiGateway::RestApi
AWS::ApiGateway::Deployment
AWS::ApiGateway::Method
AWS::Lambda::Permission
AWS::Lambda::Function
AWS::IAM::Role
AWS::Logs::LogGroup	

```
aws cloudformation deploy --template-file stack.yaml --stack-name cloudwild  --capabilities CAPABILITY_NAMED_IAM
```

### Validate
APIID=aws apigateway get-rest-apis --output text --query "items[?name=='my-api'].id"`
URL="https://${APIID}.execute-api.${AWS_REGION}.amazonaws.com/call"
curl -X POST $URL
  
### Clean up
```
aws cloudformation delete-stack --stack-name cloudwild
```
