# CloudWild

Experiment with CloudFormation and serverless backends

Credit for where I started [template example](https://bl.ocks.org/magnetikonline/c314952045eee8e8375b82bc7ec68e88)  

### Template currently provides:
- API Gateway to call Lambda via POST.
- Lambda that echos user's IP address.

### Setup
- AWS cloudshell
- git clone <this-repo>
  
### CloudFormation command
```
  aws cloudformation create-stack --stack-name cloudwild --template-body file://stack.yaml
```
  
