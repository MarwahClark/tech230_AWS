### setting up your nginx on AWS.

- once you have logged onto AWS, search for EC2 in the searchbar. EC2 is the virtual machine we will use in AWS.
- launch a new instance![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/25891c22-0889-497d-8829-5f4bb415fd69)
- name you instance following a general rule of class,name and brief description. the name should let us know what the instance does
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/5f80772b-ad70-457a-ae30-16842ad7e63b)
-once you have named your instance scroll down to operating systems and press ubuntu
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/b99bbe89-be94-4c9c-b043-250f2cc62ca5)
-select the server ubuntu 20.04
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/a0720db1-a69a-4a3f-871a-b7bbecffb36c)
-Because we only require a small machine select the t2.micro instance type
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/8335b760-7676-48a9-8e01-de707837e1e4)
-select a key pair in this case we will use the tech230 key pair as thats the one we made earlier
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/a4f4bc5c-d2cc-400e-b0f3-5cb0aebb8e9f)
-when you arrive at network settings, press edit so we can chnge our firewall/ security group
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/2e8ed89e-737f-4032-9cbf-719393dc50ed)
-name your security group and add a brief description. keeping in mind the naming conventions
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/d612f1ca-f0a8-4f5b-90af-ca484594e2b2)
- keep the source as anywhere
 ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/fb798313-9440-4c8c-a58c-9ba7def7282c)
-the summary will tell you everything you have done so far, and what file etc. that you are using
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/d8b465d3-cbb2-4f88-97b5-b37ff79c6d3c)
-press launch instance to launch
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/e6c96e81-f6c4-49bd-8543-0f64dea4a56a)
-you should then see this message
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/79c40361-61f5-4f36-a108-58f95fc47b52)
-to check you instances are running press on the instance tab at the top
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/d319acb8-938a-4949-bc9c-81abf8e543fa)
-you should see running
-press on the instance id relevant to your instance
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/eba97bb0-5e84-419d-84e7-31d75b6b0824)
-select connect to connect your ssh
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/567f2c81-737a-4cad-8607-31d519f1c901)
- run the command in your gitbash, in the .ssh folder `chmod 400 tech230.pem` the tech230.pem is your file name
-![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/17491687-2f6c-4c7c-a2c2-b2cca7f7771b)
- it will then print this message
- ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/5baf748a-d6af-4c5f-b310-1c854293c73f)
-to see all the permisssions run the code `ls -l`
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/302aeed9-d78a-4bb4-8c00-2533e1b9e139)
- next run the code `ssh -i "tech230.pem" ubuntu@ec2-54-216-134-223.eu-west-1.compute.amazonaws.com` as it autogenerates the command
- this code allows you to create a fingerprint and enter your ec2.
- ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/cd0d904e-2bd7-48aa-9939-a97928c542e7)
- ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/a5bf39b8-b817-4a0e-9fd0-250d66b864bb)
### next you have to start nginx
- run the code `sudo apt-get update -y` `sudo apt-get upgrade -y`
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/7f74f56d-f760-47e5-91bb-5f110b65c97c)
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/73e68b42-3b4a-4417-8078-f3b672ac1fd2)
- next `sudo apt install nginx -y`
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/23a7d142-5ef3-4a91-a526-3d652c29bd82)
- finally the last 2 codes `sudo systemctl start nginx` ` sudo systemctl enable nginx`
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/de985c7e-3e1c-453d-ab84-71f98250b16f)
- if you want to check the status run the code `sudo systemctl status nginx` and you should see this
- ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/1ce2408e-f522-45ed-8cb2-e7c44b5ff5fc)
- in order to get it to work you have to configure it to http and https
- you do this by going back into aws and selecting the security drop down
- ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/c0bab1f9-6929-48ed-8c99-ba2779b98868)
- it should then give you the option to enter inbound rules ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/97ce8b62-d312-4a84-b0e7-684fe3dee380)
-select your security group this will allow you to add rules![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/a34392e3-d385-472b-8134-2feea5be9f9b)

- press edit inbound rules ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/6de8e0e1-99f7-4721-9c9b-e2f927ff70e6)
- select http and change the source to 0.0.0.0
-![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/5ce634ac-5021-476f-8762-a709b5bb2a8a)
- you should see this once you save and close ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/613dd425-3133-4326-a40b-69a58170285e)
- take the public ip address from the AWS and test it out
- ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/9712de3c-f068-4283-b70f-58663453519b)
you should see this
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/6331c4e8-f473-42f2-b69b-561fa37d19d5)
- to terminate your instance, press terminate in the instance status
- ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/e149549b-79c1-447d-bbac-f90384886d30)
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/5070d8d5-aedc-495e-b671-f97da06d202f)

### setting up mongodb
-following the previous steps on how to create an instance, create a new instance and instead of writing out the nginx commands in the git bash termianl run the mongodb commands.
`#!/bin/bash`

`sudo apt update -y`

`sudo apt upgrade -y`

`sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927`

`sudo apt install mongodb -y`

`sudo systemctl start mongodb`

`sudo systemctl enable mongodb`


![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/bf971016-a34a-4b46-998a-7fd2a86107b5)

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/3a70928f-c0be-41ca-b540-f2b699658d57)

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/7645564d-10be-4776-8562-028e4d87a877)


![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/68431d88-e127-4066-bfa7-94d23b812e70)

- to check that it has worked run the ` sudo systemctl status mongodb` in the gitbash terminal and you should see `active running`
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/33e3428c-67c8-49e4-8f64-bcb7409bfb4a)


### how to create an AMI

- in order to create an AMI make an instance following the instructions from before. when you hvae created your instance, in the actions drop down select image and templates and then create template from instance.
- 
 ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/2f8de42a-9c8b-47f5-af5c-674ede4dc74e)
 - name and describe your instance
 - 
 - 
 - ![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/a9a643e0-0351-4f39-bb8e-62efd4b7993a)
 - 
 - scroll to the advanced settings option and enter user data that includes the commands to start nginx/ mongodb
 - 
 -![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/12ed4550-6abf-456d-a36d-0a28eceae252)
 
- finally launch 

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/4328433e-2669-476e-8fda-cfd157e6913e)


### deploying your app
- once you have set up your 2 instances 
- in your git bash terminal enter the folder that your app is in and run the code
`scp -i "~/.ssh/tech230.pem" -r app ubuntu@<insert your ec2 Public DNS here>:/home/ubuntu`
this will move your app contents to the home page on ubuntu, your screen should look something like this as it loads, baring in mind it will take a moment.

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/f3a27962-5370-47b5-b535-64a46b49da65)

-once you have unloaded, enter your ssh using the code `ssh -i "~/.ssh/tech230.pem" ubuntu@<insertyourdns>

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/bd2ea3f1-2e82-4335-a8b5-91f96af07a54)

- next install all the neccessary apms using these codes 
`sudo apt update`
`sudo apt install -y nodejs npm`
`sudo npm install -g pm2`
to check your pm2 installed run the code `pm2 --version`
`cd app` to enter your app file
`pm2 start app.js` this allows your app to start

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/fb78f969-f8f3-4cb1-b8f2-268644129938)

- to get your app working you have to enter the security group and add a new inbound rule at port 3000 source 0.0.0.0

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/547596eb-4698-4183-8e38-502c3b70205b)

-finally your app should be up and running when you open with the public ip address add the `:3000`

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/ed1f788b-0ea7-4bb4-829b-20ff5f5c07c0)

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/9db35bf0-1d06-4c29-bd7e-f5734f6565f7)

### Adding the 'app' directory to the EC2 instance
-Navigate to the .ssh folder on bash
- connect to the ssh while in the correct folder using `scp -i "~/.ssh/tech230.pem -r app ubuntu@<Insert your EC2 Public DNS here>:/home/ubuntu`
- to install the app run the codes
`sudo apt update`
`sudo apt install -y nodejs npm`
`sudo npm install -g pm2`
Use `pm2 --version` to verify pm2 installation
pm2
`cd app`
`pm2 start app.js` to run the app in the background
- in order to get the aws to work on the right port change the Security group to include a custom access to port 3000, for all 0.0.0.0. You can also change the SSH rule to only accept your IP.
-Use the public IP address to get to the deployed webpage.

### How to make an AMI for the running app
- While the EC2 instance for running the app is running to create the AMI select the 'Actions' drop down and click 'Create an image' 
- follow the instructions and name it and give it a description to explain roughly what it it
-Launch the AMI from Images/AMIs OR the on the same 'Launch instance' page instead of 'Quick Start' select 'My AMIs' on AWS and then log in to the EC2.
- `cd app`
-  `pm2 start app.js` to start the app
- double check that youre using the Public IP address in your web browser, then add ':3000' and you should see the Sparta Provisioning Test Page from the running app.

### How to link the posts page

- Launch  both the AMIs for the database and the app.

-Change security groups:
Add inbound rules to MongoDB EC2 instance so that the App EC2 instance can connect with it. (port 27017 for MongoDB)

-Add inbound rules to App EC2 instance so that it can connect with the MongoDB EC2 instance.

-Connect/login to both EC2 instances using the SSH method..

-run the following commands in your EC2 instances to configure to the approporiate files and environment variables:

-Check that the MongoDB is running with `sudo systemctl status mongodb` on your Database EC2.

# in EC2 for database
` sudo nano /etc/mongodb.conf` and change the ip address to 0.0.0.0 so that anyone can connect
`sudo systemctl restart mongodb`
`sudo systemctl enable mongodb`
If Nginx is not installed and running on your App EC2 follow the steps detailed earlier in this markdown to set it up. And if you use ls and the 'app' directory is not in the EC2 instance then follow the steps detailed earlier in this markdown to get it onto the EC2 before continuing.

# in app
'export DB_HOST=mongodb://<Place MongoDB EC2 IP here>:27017/posts' >> /home/ubuntu/.bashrc this will work with either private/public IP

`source .bashrc`

`cd app`

`npm install`

`pm2 start app.js --update-env` this command tiwll allow the app to start






