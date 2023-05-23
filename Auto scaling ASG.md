#### HOW TO MAKE AN ASG

- launch a template from instances using an ami
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/0173b731-f30e-48b4-903c-03d2096d0f81)

in the user data of the template place this code in

`#!/bin/bash`

 

`# navigates into the correct directory`
`cd /home/ubuntu/app`

 

`# installs app`
`npm install`

 

`# Runs/Starts the app in the background`
`pm2 start app.js`

-after you have ensured all the security groups and keys are up to standard save and launch tenmplate

