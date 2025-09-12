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

### SCALE OUT POLICY

1. Select your ASG and click on 'Automatic scaling' tab, and click 'Create dynamic scaling policy''

![](./img/Pasted%20image%20(22).png)

2. Select 'simple scaling' for policy type. Add a policy name. In this case 'highCPU' (since it is for high CPU usage).

![](./img/Pasted%20image%20(23).png)

3. Click 'Create a CloudWatch alarm'. Opens a new page.

![](./img/Pasted%20image%20(24).png)

4. On the new page, click 'select metric'

![](./img/Pasted%20image%20(25).png)

5. On the popup page click 'EC2'

![](./img/Pasted%20image%20(26).png)

6. On Select metric window, click 'By Auto Scaling Group'

7. Since you are focusing on the  CPU usage, check 'CPUUtilization' and, click 'Select metric'

![](./img/Pasted%20image%20(27).png)

8. Verify Metric name(CPUUtilization), ASG(myASG). Set period to 1 minute for quick activation.

![](./img/Pasted%20image%20(28).png)

9. Scroll down. Set Threshold type to 'Static'. Choose(Greater/Equal) and, threshold value '50'. However, all these parameters depends on business goal. Click "Next".

![](./img/Pasted%20image%20(29).png)

10. Set Trigger state to "In alarm". Since you did not create SNS, click create new topic. Add a topic name, add an email address, scroll down and click 'next'

![](./img/Pasted%20image%20(30).png)

11. A confirmation of your policy should come up showing the name and notification email.

![](./img/Pasted%20image%20(32).png)

12. Now scroll down and click 'Next'.

![](./img/Pasted%20image%20(31).png)

13. Add alarm name and description. Then click 'Next'.

![alt text](./img/Pasted%20image%20(33).png)

14. Preview Alarm settings and  click 'create alarm'

![alt text](./img/Pasted%20image%20(34).png)

15. You should see a suceess page. Though it indicates incomplete "insufficient date"

![](./img/Pasted%20image%20(35).png)

16. you have to go back to your scaling policy to finish creating it. Head over to the page. Policy type should be 'simple scaling', add a name for the policy. Select the highCPU alarm you have created earlier. Click "Create"

![](./img/Pasted%20image%20(37).png)

### Scaling policy is now complete

![](./img/Pasted%20image%20(38).png)

### SCALE IN POLICY

1. Back to your ASG page. Click "Create dynamic scaling policy"

![](./img/Pasted%20image%20(39).png)

2. Click 'Create a CloudWatch alarm' to create one for this policy(Opens a new page).

![](./img/Pasted%20image%20(40).png)

3. Click "select metric" to continue. 

4. Click "EC2", " By Autoscaling Group", and Select "CPUUtilization". Scrol down and click "Select metric"

![](./img/Pasted%20image%20(41).png)

5. Be sure your ASG is in the "AutoScalingGroupName", set "period" to 1 minute.

![](./img/Pasted%20image%20(42).png)

6. Leave "Threshold type" as "Static", Select "Lower/Equal" then Threshold value as 30 and click "Next".

![](./img/Pasted%20image%20(43).png)

7. Select "In alarm" for state trigger, select an existing SNS and select SNS created when you were creating the previous policy.

![](./img/Pasted%20image%20(44).png)

8. Scroll down and click  "Next".

![](./img/Pasted%20image%20(45).png)

9. Add a name and description for the Alarm click  "Next".

![alt text](./img/Pasted%20image%20(46).png)

10. Review/Preview and click "Create alarm"

![](./img/Pasted%20image%20(47).png)

11. Your Alarm creates successfully.

![](./img/Pasted%20image%20(48).png)

12. Head back to the policy page to complete the policy. Set Policy type to "simple scaling", add a name, then select the cloudwatch alrm you created(lowCPU). Set action to remove and number to 2. Now click create.

![](./img/Pasted%20image%20(49).png)

### Yur policy is now complete.

![](./img/Pasted%20image%20(50).png)

## Attach Application Load Balancer to Auto Scaling Group.

1. On the ASG page, click 'Load Balancers'

![](./img/Pasted%20image%20(53).png)

2. Click on "Create load balancer" to begin creating one.

![](./img/Pasted%20image%20(51).png)

3. AWS has 4 load balancing services. Click 'create' on the Application Load Balancer  tab.

![](./img/Pasted%20image%20(52).png)

4. Provide a name for the load balancer(LB). Click internet facing. Select dual stack if you are using ipv6 otherwise select ipv4.

![](./img/Pasted%20image%20(54).png)


