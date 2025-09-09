# Auto-Scaling-ALB
## This project will demonstrate how to creat Auto scaling group, and Application Load Balancer in AWS using launch template.

## Create Launch Template 

1. Head over to your AWS console EC2 home page. 

![](./img/Pasted%20image.png)

2. On the left pane select 'Launch Templates', then move towards the right and click 'create launch template'

![](./img/Pasted%20image%20(2).png)

3. Setup a name for the template. Add a description(optional).

![](./img/Pasted%20image%20(3).png)

4. Select an image for the template.

![](./img/Pasted%20image%20(4).png)

5. Select instance type. Add or create a key pair.

![](./img/Pasted%20image%20(5).png)

6. Select existing or create a security group.

![](./img/Pasted%20image%20(6).png)

7. Leave volumes at default and, click "create launch template" bottom right.

![](./img/Pasted%20image%20(7).png)

8. You should see a succes page indicating launch template was successfully created.

![](./img/Pasted%20image%20(8).png)

## Setup Auto Scaling Group(ASG).

1. head over to the EC2 overview and click Auto Scaling Groups(Towards botton left).

![](./img/Pasted%20image%20(9).png)

2. On the next page click "Creat Auto Scaling group"

![](./img/Pasted%20image%20(10).png)

3. Add a name for the ASG and select the launch template you created previously and click "next".

![](./img/Pasted%20image%20(11).png)

4. Specify VPC, Availability zone and check "Balanced best effor", then click 'Next'

![](./img/Pasted%20image%20(13).png)

5. Click "Next" if you don't want optional health check.

![](./img/Pasted%20image%20(14).png)

6. Set desired capacity, min desired, and max desired capacity.

![](./img/Pasted%20image%20(15).png)

7. Select target tracking scaling policy. Leave the Metric, target and instance warm at default.

![](./img/Pasted%20image%20(16).png)

8. Leave 'Additional capacity settings' at default. Click 'Next'

![](./img/Pasted%20image%20(18).png)

9. Add tags if you desire, otherwise click "Next" to continue.

![](./img/Pasted%20image%20(19).png)

10. Review and click 'Create Auto Scaling group'

![](./img/Pasted%20image%20(20).png)

### You should see your auto scaling group created succeefully.

![](./img/Pasted%20image%20(21).png)

## Configure Scaling Policies.









