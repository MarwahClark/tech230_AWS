vpc
virtual public cloud, mix of the 2 
ramon diagram 
![Screenshot 2023-05-23 142408](https://github.com/MarwahClark/tech230_AWS/assets/133018482/58e76eb6-808d-462e-ba35-85e1194226ef)


### CREATING VPC

- step one select the AWS VPC option in search bar. Once you have enterd select the creat a VPC button

- step two select VPC only and in the CIDR block select the `10.0.0.0/16`

- step three next we creat the internet gateway. by selecting the internet gateway option in the side bar.

- step four create a gateway and select an appropriate name

- step five next we have to connect the internet gateway to the VPC. this is done by pressing the `attatch to vpc` button in the actions folder

- step six once you hvae pressed this you can select your VPC by searching for your VPC name. once it has attatched to the Internet gateway state will change to `attached`

- step seven now we have to create the subnets. Again select the subnets option in the sidebare and create subnet.

- step eight select your VPC, then give a suitable name so you can tell the difference between private and public subnet. the CIDR block should be `10.0.2.0/24`

- step nine create your route table by clicking route tables in the sidebar and `create route table`

- step ten select a suitable name and pick your VPC. go to the subnet association tab.

- step eleven select edit subnet associations and select the public subnet so that it associates with our route table.

- step twelve, adding routes. add a route with the ip addrees 0.0.0.0/0, add a route for HTTP, port 3000 and 80

![Screenshot 2023-05-23 153825](https://github.com/MarwahClark/tech230_AWS/assets/133018482/4eb5db23-ac1d-4f0b-8f97-a16ef4de3b25)
![Screenshot 2023-05-23 153920](https://github.com/MarwahClark/tech230_AWS/assets/133018482/5d395a68-f595-4f65-9e24-61cf8ec8fbd3)
![Screenshot 2023-05-23 154004](https://github.com/MarwahClark/tech230_AWS/assets/133018482/f71b8d8f-fffd-4f91-be4c-76084562caf9)

- step thirteen next connect your instances to the vpc, adding the comands for nginx into user data.
  by creating an instance, however once at the network settings selecct your VPC and subnet. you will also have to create a new security group as your previous security group will not be compatioble as it has to be in the same VPC as the subnet.
  
  ![Screenshot 2023-05-23 154113](https://github.com/MarwahClark/tech230_AWS/assets/133018482/a443ee79-5f4f-47aa-8882-bdddac98967c)

