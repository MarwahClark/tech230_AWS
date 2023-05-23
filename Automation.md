### Automation of reverse proxy

-first create your ssh connection using aws command `ssh -i "tech230.pem" ubuntu@<yourdsn>`

- create a provision file in your app folder using either `touch provision.sh`  or `sudo nano provision.sh`

- copy and paste your previous provision script using the shebang

`#!/bin/bash`

`sudo apt-get update -y`

`sudo apt-get upgrade -y`

`sudo apt-get install nginx -y`
`sudo systemctl start nginx`
`sudo sed -i 's+try_files $uri $uri/ =404;+proxy_pass http://localhost:3000/;+' /etc/nginx/sites-available/default


`sudo systemctl enable nginx`
`sudo systemctl restart nginx`

`sudo apt install sed -y`
`sudo apt-get install git -y`
`curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -`

git clone https://github.com/MarwahClark/app.git
sudo apt-get install nodejs -y
sudo npm install pm2 -g

`echo 'export DB_HOST=MONGODB://172.31.58.198:27017/posts' >> .bashrc`
`source ~/.bashrc`

`cd app`
`pm2 stop app.js`
`pm2 start app.js --update-env`

- run this provision file using the code `./provision.sh` if it doesnt allow, run `sudo chmod a+rwx /.provision.sh` to allow for all permisions

- test the provision file again by running the code `./provisons.sh` if successful it should show `your app is ready and listening on port 3000`
- 

![Screenshot 2023-05-22 185015](https://github.com/MarwahClark/tech230_AWS/assets/133018482/0e845b2c-29dd-4307-b71d-ca6ed7c203fb)



also double check your etc file by runnning 
`sudo nano /etc/nginx/sites-available/default`

and if not there already add 
`server {`
    `listen 80;`
    `server_name _;  # Replace with your domain or IP address`

    `location / {`
        `proxy_pass http://localhost:3000/;`
        `proxy_set_header X-Real-IP $remote_addr;`
        `proxy_set_header Host $host;`
        `proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;`
        `proxy_set_header X-NginX-Proxy true;`
        `proxy_http_version 1.1;`
       ` proxy_set_header Upgrade $http_upgrade;`
      `  proxy_set_header Connection "upgrade";`
 `   }`
`}`


this was my main blocker as i didnt have this file. 
after this run `./provision.sh` to run your provision file previously

it should take you directly to the sparta app page
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/93a17076-c2b6-4a6e-9a41-badfc7ad614b)

create an ami image of this to save

