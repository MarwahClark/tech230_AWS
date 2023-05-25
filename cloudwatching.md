### what is cloudwatching
cloud watching is monitoring and managing the various applications in AWS. With cloud watching you are able to set alarms and triggers to notify you when you have used more than you should for example monitoring CPU utilisation on cloud machine, at some point you want a trigger so that you know when youve hit your target budget/ workload (where we may need to increase or decrease amount of instances)

consequences of not having cloud watch, instances could be overloaded and people using may not be able to load them quickly and the instances can fail. to avoid that happening tou have to work out the point in which you need an alarm so that more instances can be created via autoscaling.

if traffic goes down we may also want to cut down the amount of services running so that the business doesnt lose money.


![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/35f1d243-c8ff-4e6b-9b77-dc4a0965cc4a)

### How to set up monitoring

- set up a working instance e.g one you previously used for nginx or app 

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/618a9308-a342-4914-bd76-31c96412cd35) 

-. once your instance is up, scroll down to the monitoring section and select manage monitoring.
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/a20f3433-84a4-4aab-8db7-ffd66aed180d)

### making a dashboard
- select the add dashboard 

-![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/0cf32604-f72f-4301-8624-8d5e11747088)

- name your dashboard appropriartly
-![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/2e2b04eb-3e6c-4aa8-933d-10ccd04f0f9a)

-Once you have named your daashboard, select how you want to see the information.
![Screenshot 2023-05-25 143503](https://github.com/MarwahClark/tech230_AWS/assets/133018482/43a67875-d773-4a30-8559-4784ab7514e6)

-select 'empty' and you should see this
![Screenshot 2023-05-25 143518](https://github.com/MarwahClark/tech230_AWS/assets/133018482/b9d9fa36-7018-4aa6-b1ec-8e86c325d1cc)

### setting up CPU usage alarm
- open the cloudwatch console at  https://console.aws.amazon.com/cloudwatch/ ensuring your location is still in ireland
- you should see a navigation panel, select `alarms` > `all alarms` 

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/1524a1d7-1658-4c34-a285-73bef8c76bf6)

- next step you create your alarm using the create alarm button
- It will then ask you to specify metric and conditions
- ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/d99f0e86-7ab0-497a-8a9c-4f4a648f5af7)

- here you can select the alarm threshold and the metric expression this is where you will pick `EC2> Per-instance Metrics`

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/678fe34e-fa86-4545-a599-24b59cac37e9)

- select the instance that you want to monitor using your instance ID and the `CPU-Utilization` and press select metric
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/e87082d5-c9b1-4664-af98-ade2600332bb)

- select `specify metric conditionos` and pick the `statistic` and `average` option
- choose a time period
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/bfcfa2a5-c0a3-4a19-b3a3-4b0e076d35c0)

- for threshold type `select static`
- for whenever CPUUttilization is select `Greater` under than select the threshold that you want to trigger the alarm
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/a44afee2-b878-480f-8766-6c279ddbfbc8)

- under additional config select the configuration for data points requiered for the alarm to be triggered when in ALARM state. if the two are identical then an alarm will be generated when that soecific number of consecutive periods exceed the thershold
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/497b6d64-9194-4c82-894e-7891cc447481)

- under notification select `in alarm` and `SNS topic` so that it can notify you when the alarm is triggered. here you can add your email address so that emails are sent to you when triggered
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/9df8c834-a7e6-46b5-9d7e-60b012ee6eb3)

-Finally name and describe your alarm
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/fdced735-9564-470e-a058-be906909be2a)

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/aafb9546-6943-482e-9b88-0db94f2428cb)

this is the preview of what youre dashboard should look like with the alarm 
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/e798e4f9-06ec-4022-bc23-17a826d3a2aa)




-
