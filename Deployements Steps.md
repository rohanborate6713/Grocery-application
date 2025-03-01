# Grocery application Deployment

# 
- Create an EC2 Server (ubuntu) and connect to that Server.
## Backend  Deployment 
- Clone the  frontend of application (GroceryAppBE) from GitHub.
```
git clone https://github.com/AnupDudhe/GroceryAppBE-.git
```
- You can also fork this repository to your GitHub account and then clone .


![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/xHJfdXPHjWX21OeVLUBq4.png?ixlib=js-3.7.0 "image.png")

- Here in this deployment we are deploying frontend , backend on the same server 
- This is an node js based application we have to install node js and npm (node package manager)
```
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs
```
- **npm (Node Package Manager)** is the default package manager for **Node.js**. It is used to install, manage, and share JavaScript packages (also called **modules** or **libraries**) in a Node.js environment.
- [﻿Node.js](https://nodejs.org/)  (LTS version recommended)
- **npm** (Comes with Node.js)
- `curl`  → Downloads the script from NodeSource.
- `-f`  → Fails silently on errors.
- `-s`  → Runs in silent mode (no unnecessary output).
- `-S`  → Shows errors if any occur.
- `-L`  → Follows redirects.
- Pipes (`|` ) the downloaded script to `bash`  for execution.
- `sudo -E`  → Runs the script as **root** while preserving environment variables.
- `bash -`  → Executes the script directly.


- `sudo apt install -y nodejs` 
    - `sudo`  → Runs the command as root.
    - `apt install`  → Installs the specified package.
    - `-y`  → Automatically says "yes" to installation prompts.
    - `nodejs`  → Installs Node.js (along with npm, which comes bundled).


![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/s7HWfs0jLwQauce5dHlpY.png?ixlib=js-3.7.0 "image.png")

![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/2PR-UCbspl8rgYeQg8W8b.png?ixlib=js-3.7.0 "image.png")



- Check node js and npm  is installed or not 
```
npm -v
```
```
nodejs -v
```
---

## Install Database 
- we are using mongoDB , install it from below link
```
[﻿www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/) 
```
#### Install MongoDB Community Edition
#### Import the public key.
```
sudo apt-get install gnupg curl
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/6BY7fvHmpdLNHUnVR2KIP.png?ixlib=js-3.7.0 "image.png")

- To import the MongoDB public GPG key, run the following command:
```
curl -fsSL https://www.mongodb.org/static/pgp/server-8.0.asc | \
sudo gpg -o /usr/share/keyrings/mongodb-server-8.0.gpg \
--dearmor
```
#### Create the list file.
- Create the list file `/etc/apt/sources.list.d/mongodb-org-8.0.list` for your version of Ubuntu.
```
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-8.0.gpg ] https://repo.mongodb.org/apt/ubuntu noble/mongodb-org/8.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-8.0.list
```
#### Reload the package database.
```
sudo apt-get update
```


![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/NkB5BILlGuhAucGTzoOWR.png?ixlib=js-3.7.0 "image.png")

#### Install MongoDB Community Server
```
sudo apt-get install -y mongodb-org
```


![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/WmTtxH6hmNvLSS9muJFk8.png?ixlib=js-3.7.0 "image.png")

- check mongodb database is installed or not 
```
mongod --version
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/WE3Dp3hBzStP19BIp-1DS.png?ixlib=js-3.7.0 "image.png")

- start and enable the mongodb database service
```
systemctl status mongod
```
```
sudo systemctl start mongod
```
```
sudo systemctl enable mongod
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/vocnLJ68SORt8KYBlOda7.png?ixlib=js-3.7.0 "image.png")



![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/yaaHHR9VV03qlplnK3u47.png?ixlib=js-3.7.0 "image.png")



#### Connect to the mongodb database
```
mongosh
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/hT_-5E-jXcfKnzgWvAtmj.png?ixlib=js-3.7.0 "image.png")

- go to our database and check any data in available or not 
```
use grocerydb
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/3SCkfVLTR_-AJ5nXb5cdJ.png?ixlib=js-3.7.0 "image.png")

- currently we don' t have any data in database
- to exit from the database use `﻿exit`  command


---

#### Install pm2 for daemon service running on server
- **PM2** (Process Manager 2) is a **production-grade process manager** for Node.js applications. It helps you:
- ✅ **Keep applications running continuously** (auto-restart on crashes).
✅ **Manage multiple applications** with process monitoring.
✅ **Auto-restart on system reboot**.
✅ **Log and monitor CPU/memory usage**.
✅ **Run apps in the background** (as a daemon).
```
sudo npm install -g pm2
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/JtxGNOyHBIqZiV2OWD5HU.png?ixlib=js-3.7.0 "image.png")



#### Start the node js application with pm2
```
cd GroceryAppBE-
```
```
pm2 start server.js --name grocery-backend
```
- `**pm2 start server.js**`  → Starts `server.js`  in the background as a managed process.
- `**--name grocery-backend**`   → Assigns a custom name **"grocery-backend"** to the process for easier management.
- Saves the currently running PM2 processes.
```
pm2 save
```
- Enable Auto-Start on System Reboot
```
pm2 startup
```
- List Running PM2 Processes
```
pm2 list
```
- Other pm2 commands
```
#pm2 stop grocery-backend  will stop your pm2 backend api 
#[PM2] Freeze a process list on reboot via: few additional commands  
#$ pm2 save

#[PM2] Remove init script via:
  #$ pm2 unstartup systemd
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/VSvlx6CugLc9Ci4BYDZjS.png?ixlib=js-3.7.0 "image.png")

- now our applications backend service is running (running in background).
- Try to access backend service with public IP and port 5000
- Application is hosted on port no 5000 , so you have to enable this port in security groups
```
http://<your-server-publicIP>:5000
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/sF35odkcJbFzF55Algw84.png?ixlib=js-3.7.0 "image.png")

- we are running backend only , so getting this .
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/E11Hz_I5S1WtqncBB_8AH.png?ixlib=js-3.7.0 "image.png")



---

## Frontend Deployment 
- Clone the  frontend of application (GroceryAppFE) from GitHub.
```
git clone https://github.com/AnupDudhe/GroceryAppFE.git 
```
- You can also fork this repository to your GitHub account and then clone .
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/nIWX2ZnwGECx5YOeRD-Rs.png?ixlib=js-3.7.0 "image.png")

- we are using same server for frontend and backend so node js and npm is already installed on our server, if you are running on separate server you need to install node js and npm
- Before stating our frontend server we have update our server public IP in .env file in frontend application
```
cd GroceryAppFE/
ls -a 
```
- we get the .env file update public IP with your server public Ip
- `REACT_APP_API_URL=http://35.192.28.119:5000` 
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/n8q1O7ieBy70pMXiDWDBl.png?ixlib=js-3.7.0 "image.png")

- install npm and then Start the application with node package manager (npm)
```
npm install
```
```
npm start
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/MpLPnY7X9NzxHu88QbKBz.png?ixlib=js-3.7.0 "image.png")



![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/q1denT3B2aGI-SGWBBukP.png?ixlib=js-3.7.0 "image.png")

- frontend application is started 
- to check it is running , open your browser and try with below URL
```
http://<your-server-publicIP>:3000
```
- Application is hosted on port no 3000 , so you have to enable this port in security groups


![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/KyTGWFujyTYJvD1npsyWn.png?ixlib=js-3.7.0 "image.png")



- To check it is running , open your browser and try with below URL
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/1pl7cN-a0MmjHtzskIzlf.png?ixlib=js-3.7.0 "image.png")

- add some data in grocery list
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/z6DllkBarM7eBkJnFJFdl.png?ixlib=js-3.7.0 "image.png")

- now connect to the database and check database is updated or not
- note - frontend service is not running in background so you have to connect our server , take server access from another window


![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/lEjj-ISBZ8dTvhST1bm_Z.png?ixlib=js-3.7.0 "image.png")



- remove any value from database. 


![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/X-Yn3sNFfqSmp6Bd_06ub.png?ixlib=js-3.7.0 "image.png")



- Database is updated 
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/54lRctg2HLlpDQ5a5T3cb.png?ixlib=js-3.7.0 "image.png")



---

## Deploy same application on nginx


- Our application backend service is already running
- we are deploying frontend with nginx
- to deploy the application need to create build using npm
```
﻿cd GroceryAppFE/
npm run build 
```


