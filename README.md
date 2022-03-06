# CloudWild

## AWS CDK appraoch
Cloudshell environment fails due to the inability to use spawn
Debian instructions
```
sudo -i
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
. ~/.nvm/nvm.sh
nvm install node
node -e "console.log('Running Node.js ' + process.version)"
npm install -g aws-cdk

```

```
# clone solutions-contructs
git clone https://github.com/awslabs/aws-solutions-constructs.git
cd aws-solutions-constructs/source/use_cases/deployment
# Set the proper version numbers in the package.json file
../../../deployment/align-version.sh
# Install dependencies
npm install
# Build the use case
npm run build
# Deploy the use case
cdk deploy

```

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
