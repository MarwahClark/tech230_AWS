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
- step thirteen next connect your instances to the vpc  by creating an instance, however once at the network settings selecct your VPC and subnet. you will also have to create a new security group as your previous security group will not be compatioble as it has to be in the same VPC as the subnet.
