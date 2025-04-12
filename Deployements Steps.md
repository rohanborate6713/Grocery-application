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



```
https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/
once mongodb is installed ensure you make a change in /etc/mongod.conf
vim /etc/mongod.conf
ensure you make this change in the configuration file
# network interfaces
net:
  port: 27017
  bindIp: 0.0.0.0
```
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


- If your database hosted on another server , then try to get access from your server to database server
- note --> you also required to install mongod on your server as it works as a client
```
mongosh "mongodb://<database_server_ip>:27017"
```
---

#### Pre-requisite to deploy application 
```
npm install
npm init -y
npm install express mongoose cors
npm install dotenv
npm install portfinder

########
portfinder is a utility module in Node.js apps that helps you find an 
available port on your machine —
especially useful if you're not hardcoding the port number.
```


---

#### Install pm2 for daemon service running on server
- **PM2** (Process Manager 2) is a **production-grade process manager** for Node.js applications. It helps you:
- ✅ Keep applications running continuously (auto-restart on crashes).
✅ Manage multiple applications with process monitoring.
✅ Auto-restart on system reboot.
✅ Log and monitor CPU/memory usage.
✅ Run apps in the background (as a daemon).
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
npm install
npm install dotenv
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



- Remove any value from database. 


![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/X-Yn3sNFfqSmp6Bd_06ub.png?ixlib=js-3.7.0 "image.png")



- Database is updated 
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/54lRctg2HLlpDQ5a5T3cb.png?ixlib=js-3.7.0 "image.png")



---

## Deploy frontend of  Grocery-application on pm2
```
npm install
npm run build
pm2 list
pm2 serve build/ 3000 --name "grocery-frontend" --spa
```
---

## Deploy frontend of  Grocery-application on nginx


- Our application backend service is already running in background, if not running please start 
- we are deploying frontend with nginx


#### Nginx Installation
```
sudo apt update
sudo apt install nginx -y
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/6aWCp_ZDWFyd2KxYzKfke.png?ixlib=js-3.7.0 "image.png")

- check nginx is installed or not 
```
nginx --version
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/Gf2-3XqYQ9rD0uBp3SSdw.png?ixlib=js-3.7.0 "image.png")



Deploy a Frontend Build

- Now go to frontend app folder 
- To deploy the application need to create build using npm
```
﻿cd GroceryAppFE/
npm run build 
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/WHHKQ3sN4zBeG9OfH1Z31.png?ixlib=js-3.7.0 "image.png")

- build folder is created


- If your build contains **static files** (e.g., `index.html` , `.js` , `.css` ), you can serve them directly via Nginx.
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/oXmg230MioD2IDyY9By_V.png?ixlib=js-3.7.0 "image.png")



- Moves build files to    `﻿var/www/html` 
- it's the **default root directory** for websites served by **Nginx** or **Apache**.
- By placing the build in `/var/www/grocery-app`  , we ensure Nginx can access and serve the files.
#### Why Not Serve from Any other Directory?
- **Permissions**: Nginx runs as a system user (`www-data` ), so it needs access to the files.
- **Security**: Keeping site files in `/var/www/`  is a best practice.
- **Ease of Management**: Standard location for hosting static sites.


```
sudo mkdir -p /var/www/grocery-app
```
```
sudo cp -r build/* /var/www/grocery-app/
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/x3irrGPK00RXRNwRm8bte.png?ixlib=js-3.7.0 "image.png")



Configure Nginx

- Edit the Nginx config file:    --> /etc/nginx/sites-available/grocery-ap
- Nginx **doesn't know** where to serve files from by default.
Editing the config file allows us to:
    1. **Tell Nginx where the files are located** (`root /var/www/grocery-app;` ).
    2. **Define how to handle requests** (`try_files $uri /index.html;` ).
    3. **Enable Reverse Proxy (For Backends)** → Forwarding requests to a Node.js backend.
```
sudo vim /etc/nginx/sites-available/grocery-app
```
- add below server configuration in it 
- Replace  `your_domain_or_ip`  with your server public IP or domain name
```
server {
    listen 80;
    server_name your_domain_or_ip;   #- Replace  `your_domain_or_ip`  with your server public IP or domain name

    root /var/www/grocery-app;
    index index.html;
    
    location / {
        try_files $uri /index.html;
    }
}
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/7EgAtt7fHhunnUOqr79DK.png?ixlib=js-3.7.0 "image.png")

- save and exit 


Enable Configuration & Restart Nginx

```
sudo ln -s /etc/nginx/sites-available/grocery-app /etc/nginx/sites-enabled/
```
```
sudo nginx -t 
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/fQ4lp4oWkEXGaq_wS9dHG.png?ixlib=js-3.7.0 "image.png")

```
sudo systemctl restart nginx
```
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/n8nZRe2BI-SXtvkP-3TrU.png?ixlib=js-3.7.0 "image.png")



- Your frontend is now deployed on Nginx...
- open your browser and then put your server public IP and check ,our application is deployed on nginx


![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/FtiafCOGbLylfd7K9hkXZ.png?ixlib=js-3.7.0 "image.png")



- Add some items in grocery list to check functionally it is working or not 


![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/LyltbDtMXNh2kTd7NuGnL.png?ixlib=js-3.7.0 "image.png")



-  connect to database and check , it is updated correctly .
![image.png](https://eraser.imgix.net/workspaces/jv5HfVPGAthbbGqNH2wG/yuIy5hbLwHZ10ovGIULZ9qCXT8E3/lL8W-ZmAllUfsvO10ltLT.png?ixlib=js-3.7.0 "image.png")



## Troubleshooting 
- if your application is deployed but data is not added in database , or after clicking on add button 
      you `doesn't` get any response . to check locally 

```
run npn dev

chmod +x node_modules/.bin/nodemon

```





