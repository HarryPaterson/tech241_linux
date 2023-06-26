# Deploying App and Database

### Contents
* Deploy App
* Deploy Database

### Deploy App
To run an application on Azure in Linux, you can follow these steps:

This can be done using the terminal or an SSH client. The exact command will depend on your operating system and SSH client.
1. Update and upgrade first 
```
sudo apt update -y
sudo apt upgrade -y`
```


2. **Install Node.js**: Inside the VM, you need to install Node.js to run your application. You can use the following commands to install Node.js version 12.x:
```
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt install nodejs -y
```

3. **Install PM2**: PM2 is a process manager for Node.js applications. It helps in managing and running your application in the background. Install PM2 globally using the following command:
```
sudo npm install pm2 -g
```

4. **Navigate to the App Folder**: Use the `cd` command to navigate to the folder where your application is located:
```
cd /path/to/app/folder
cd app/app
```

5. **Install Application Dependencies**: Use `npm install` to install the dependencies required by your application:
```
npm install
```

6. **Start the Application**: Use `npm start` or `node app.js` to start your application:
```
npm start
```
   or
```
node app.js
```

8. **Configure Network Security Group**: In the Azure portal, configure the network security group (NSG) associated with your VM to allow inbound traffic on the required port for your application. Create a rule to allow incoming traffic on the specific port your application listens to. In our case , this is 3000

9. **Cancel or Kill the Application**: To stop the running application, you can use `Ctrl+C` in the terminal where the application is running. Alternatively, if you are using PM2, you can stop the application using the following command:
```
Ctrl^C or kill -9 PID
```
   
### Deploy Database

1. Import the MongoDB public GPG key:
```
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -
```
This command downloads the MongoDB public GPG key and adds it to the system's keyring. It is necessary for validating the authenticity of MongoDB packages during installation.

2. Add the MongoDB repository to the package sources:
```
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
```
This command adds the MongoDB repository to the system's package sources by creating a new file `/etc/apt/sources.list.d/mongodb-org-3.2.list` with the repository information.

3. Install MongoDB packages:
```
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20
```
4. Change Config to allow outside connections 
```
sudo nano /etc/mongod.conf
bindIP 0.0.0.0
```
0.0.0.0 is a security risk but is fine for testing purposes

5. Start Service and check status
```
sudo systemctl start mongod
sudo systemctl status mongod
```
6. Set enviromental variable in app for database Ip
```
export DB_HOST=mongodb://<IP-ADDRESS>:27017/posts
```
