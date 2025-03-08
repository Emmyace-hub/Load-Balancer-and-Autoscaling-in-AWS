
# Load Balancer and Auto-scaling in AWS
Understanding the fundamental concept of High Availability, Scalability, Load Balancer and Auto scaling Groups

    Auto Scaling Group (ASG) in AWS is a service that automatically manages a group of EC2 instances to ensure your application maintains the desired number of healthy instances. It helps with scalability, availability, and cost optimization by automatically adding or removing instances based on demand.

splitting the project into two parts:

*  part 1: Application load balancer

*  part 2: Auto Scaling Group


## PART 1: Application Load Balancer
 
 The first step is creating EC2 instance to host websites :
 ![1](./img/1.png)
display below are the website/ip address of the instances created:
![1a](./img/1a.png)
![1b](./img/1b.png)
![1c](./img/1c.png)

## creating a Target Group:
after creating the instances i create a target group, we have three ec2 instances in order to show how the load balance connects all of them as seen below:
![2](./img/2.png)
![2](./img/2a.png)
![2](./img/2b.png)
as we can see all instances were registered on the Target Group

![2](./img/2c.png)

## creating the Load Balancer:
The Application load balancer is used for the load balancer since we are working on a website, the following the steps below:
![3](./img/3.png)
![3](./img/3a.png)
![3](./img/3b.png)
![3](./img/3c.png)
![3](./img/3d.png)
![3](./img/3e.png)

after this process was concluded i went to the "Target Group" section to check the health status of the instances and saw it all the 3 instances where unhealthy
![4](./img/4.png) 
afterwhich i copied the public ip address"98.81.72.88" of the instance and tried to ping it from my command prompt and got a "Request time out" error which is to say the instance i was not able to connect to the instance as seen below a
![4](./img/5.png)
![5](./img/5.png)
![5](./img/5a.png)
Then i went to cross check the security group configuration of the instances inbound rules and made sure they allowed traffic from the Application load balancer, i also increased the health check Timeout & Reduce Threshold after which i tried to ping the ip address and was able to connect with it as seen blow:
![5](./img/5b.png)
![5](./img/5c.png)
![5](./img/5c2.png)
![5](./img/5d.png)

## PART 2: AUTO SCALING GROUP(ASG)

As i said earlier the ASG helps with scalability, availability, and cost optimization by automatically adding or removing instances based on demand
 The first step is creating an "ASG", we would need to create a "launch template" during the process following the steps shown below:
 ![6](./img/6.png)
 ![6](./img/6a.png)
 ![6](./img/6b.png)
 ![6](./img/6c.png)
 ![6](./img/6d.png)
 ![6](./img/6e.png)
 ![6](./img/6f.png)

 After successfully creating the launch template we go back to the "Auto Scraling Group" setting and finish the process as seen blow:
 ![7](./img/7.png)
 ![7](./img/7a.png)
 ![7](./img/7c.png)
 ![7](./img/7d.png)
 ![7](./img/7e.png)

 completing the configuration of the Auto Scaling Group i went to compy the DNS "http://new-asg-1-1065400760.us-east-1.elb.amazonaws.com/" and try loading it on my web browser whereit was able to display the content of the website and when i deleted an instance the ip address did change as seen below:
 ![8](./img/8.png)
 ![8](./img/8a.png)
 ![9](./img/9a.png)