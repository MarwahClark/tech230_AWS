### Automation of reverse proxy

-first create your ssh connection using aws command `ssh -i "tech230.pem" ubuntu@<yourdsn>`

- create a provision file in your app folder using either `touch provision.sh`  or `sudo nano provision.sh`

- copy and paste your previous provision script using the shebang

`#!/bin/bash`

`sudo apt-get update -y`

`sudo apt-get upgrade -y`

`sudo apt-get install nginx -y`

`sudo nano /etc/nginx/sites-available/default`

`sed -i 's+try_files $uri $uri/ =404;+proxy_pass http://localhost:3000/;' app-provision.sh`

`sudo nginx -t`

`sudo systemctl restart nginx`

`sudo apt-get install git -y`

`curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -`

`sudo apt-get install nodejs -y`

`npm install pm2 -g`

`cd app`

`npm install`

`npm start`

- run this provision file using the code `./provision.sh` if it doesnt allow, run `sudo chmod a+rwx /.provision.sh` to allow for all permisions

- test the provision file again by running the code `./provisons.sh` if successful it should show `your app is ready and listening on port 3000`
- 


![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/60a7c4fc-091f-4429-8d63-49e62cc65f90)


