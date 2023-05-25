### What is a VPC?

an amazon vpc is an isolated  part of AWS clouid and you can use to create a virtual network for your amazon ec2 resources, they allow you to configure your own security groups, subnets and ip address'.

 
![Screenshot 2023-05-23 142408](https://github.com/MarwahClark/tech230_AWS/assets/133018482/58e76eb6-808d-462e-ba35-85e1194226ef)


### CREATING VPC

- step one select the AWS VPC option in search bar. Once you have enterd select the creat a VPC button 

https://github.com/ahmedmujtba/tech230_aws/blob/main/assets/cr-vpc.png


- step two select VPC only and in the CIDR block select the `10.0.0.0/16`

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/e86490a6-60ad-4c0e-9da8-107437d44465)

## Creating the internet gateway 

- step three next we creat the internet gateway. by selecting the internet gateway option in the side bar.

- step four create a gateway and select an appropriate name

- step five next we have to connect the internet gateway to the VPC. this is done by pressing the `attatch to vpc` button in the actions folder

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/c8ce6746-acb7-4003-b698-6b995efe7812)

- step six once you hvae pressed this you can select your VPC by searching for your VPC name. once it has attatched to the Internet gateway state will change to `attached`

### creating subnets

- step seven now we have to create the subnets. Again select the subnets option in the sidebare and create subnet.

- step eight select your VPC, then give a suitable name so you can tell the difference between private and public subnet. the CIDR block should be `10.0.2.0/24`

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/471de85c-3578-4113-b5ce-666ccbe41a8d)

### creating route tables

- step nine create your route table by clicking route tables in the sidebar and `create route table`

- step ten select a suitable name and pick your VPC. go to the subnet association tab.

- step eleven select edit subnet associations and select the public subnet so that it associates with our route table.
- 
- ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/e88c5ed9-ddfe-4424-80f1-35d95d09d0d1)


- step twelve, adding routes. Connnect your subnet and you should see it move from the table without explicit subnet associations to with.


### Connecting the instances

- step thirteen next connect your instances to the vpc, adding the comands for nginx into user data.

-change the auto assign public IP to enable.

Once at the network settings selecct your VPC and subnet. you will also have to create a new security group as your previous security group will not be compatioble as it has to be in the same VPC as the subnet.


  
  ![Screenshot 2023-05-23 154113](https://github.com/MarwahClark/tech230_AWS/assets/133018482/a443ee79-5f4f-47aa-8882-bdddac98967c)

