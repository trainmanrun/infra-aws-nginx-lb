# infra-aws-nginx-lb

1. Create VPCs by reviewing the documents below
- https://docs.aws.amazon.com/AmazonECS/latest/developerguide/create-public-private-vpc.html
- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Scenario2.html

2. We need to have another public subnet (in the AZ where we have the private subnet) for this to work with a load balancer. So go ahead and create that. Refer why below:
- https://aws.amazon.com/premiumsupport/knowledge-center/public-load-balancer-private-ec2/

3. Create the EC2 in the Private Network. 
4. Use a Bastion EC2 in the Public subnet to connect to the EC2 in private Network 
```
ssh-add <AWS Key.pem>
ssh -A ec2-user@<Bastion EC2 in Pub NW>
ssh ec2-user@<To be ngnix EC2 in Pri NW>
```
5. Install ngnix on it 
```
sudo amazon-linux-extras install -y nginx1
sudo systemctl restart nginx
```

6. Create a load balancer by reviewing the documents below
- https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-create-https-ssl-load-balancer.html

7. In your managed hosted zones (Route 53), add a Type A record for a DNS and have that point to your load balancer.
- You can use the AWS Certificate Manager to get a [Public certificate](https://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request-public.html) as well to get the HTTPS traffic flowing.
```
http://<Route-53-A-Record-name>
https://<Route-53-A-Record-name>
```
