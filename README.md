## Configuring client IP address preservation with a Network Load Balancer in AWS Global Accelerator

This repo includes the CloudFormation template that deploys the architecture mentioned in Figure-1 below. Check out the [Configuring client IP address preservation with a Network Load Balancer in AWS Global Accelerator](https://aws.amazon.com/blogs/networking-and-content-delivery/configuring-client-ip-address-preservation-with-a-network-load-balancer-in-aws-global-accelerator/) blog post for details on the solution.

![Figure-1 Sample Architecture](architecture.png)

## PreRequisites
- You must have AWS CLI configured on the machine
- You must have the right IAM permissions to deploy this CloudFormation template

## Deployment steps

Use `aws configure` to ensure you have the correct credentials on your machine. After that, clone the repo and navigate to the directory:
```
https://github.com/aws-samples/aws-global-accelerator-client-ip-preservation-nlb
cd aws-global-accelerator-client-ip-preservation-nlb
```

Deploy the stack:
```
aws cloudformation create-stack --stack-name aga-sipp-nlb-demo \
   --template-body file://aga_sipp_nlb_cfn_latest.yaml \
   --parameters ParameterKey=AllowedIP,ParameterValue=0.0.0.0/0 \
   --capabilities CAPABILITY_NAMED_IAM \
   --region us-west-2
```

## Cleanup
```
aws cloudformation delete-stack --stack-name aga-sipp-nlb-demo  --region us-west-2
```

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

