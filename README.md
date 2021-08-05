# infra-aws-nginx-lb

1. Create VPCs by reviewing the documents below
- https://docs.aws.amazon.com/AmazonECS/latest/developerguide/create-public-private-vpc.html
- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Scenario2.html

2. Create the EC2 in the Private Network. 
3. Use a Bastion EC2 in the Public subnet to connect to the EC2 in private and get it to run ngnix 

4. Create a load balancer by reviewing the documents below
- https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-create-https-ssl-load-balancer.html

**Issue: Though the LB says that the instance is connected, the URL (of the LB) doesn't really go to the instance.**
- I tried adding another public subnet (to the same AZ that had the private subnet) and recreating the LB, but that didn't work.
https://aws.amazon.com/premiumsupport/knowledge-center/public-load-balancer-private-ec2/
