# Installation and Configuration
We will be installing the necessary software to run and manage a MongoDB database on your local machine. This file assumes you are using Microsoft Windows 10 or newer. We will be installing the following:
 - MongoDb & MongoDB Compass
 - Mongosh

After installing we will be configuring MongoDB to run in authenticated mode (requiring a username and password to connect) and we will be adding some locations to the PATH variable.

## Installing MongoDB & Compass
We want to install the MongoDB Community Server. You can find downloads for all platforms [here](https://www.mongodb.com/try/download/community). This installer includes the MongoDB database engine as well as Compass, a GUI tool for managing your databases. Installing with an MSI is simple, run the installer and continue with a default installation. We suggest installing the software as a service if possible.

Take note of the install location. On Windows 10, by default, the location will be `C:\Program Files\MongoDB\`. In that location is a `Server\<version>\bin\` folder. We will need to add that directory to the PATH variable in a later step. 

## Installing Mongosh
Mongosh is the MongoDB shell, a command line application to manage and query your Mongo databases. This download isn't an MSI, we will have to install manually. Thankfully, it isn't difficult. We just need to unzip the files somewhere, then add the `bin\` folder to the PATH variable. Choose a location on your storage volume, create a folder if necessary, and unzip mongosh there. We would suggest creating a new directory in the same location where the MongoDB server was installed, `C:\Program Files\MongoDB\`

![installation directory](..\resources\install-directory.png)

*Inside each of these directories there is a `bin\` folder which we will add to the PATH in the next steps.*

## PATH Variable
Next we need to add two locations to the PATH environment variable. PATH tells the operating system where to search for programs. If you look in the folders where we installed MongoDB and mongosh, you will find a dolfer called `bin\` which is short for "binary". This is a common convention, this is where you will find "binaries", executables and scripts. The OS needs to know these two locations so it can find `mongod.exe` and `mongosh.exe`.

Start by going to the Start menu and typing "Environment variables" into the search. 

![start menu search](..\resources\search-start-menu.png)

We want to edit the system environment variables. You will need administrator privilages to do so.

After clicking that item you will be brought to the System Properties screen, click the button at the bottom right "Environment Variables...".

![system env variables](..\resources\env-variables.png)

This will bring up the Environment Variables screen. Note that there are two sections here, System and User variables. We want the system variables. Look in that list for a variable called "Path" or "PATH". Select it and click the "Edit..." button.

This will bring up the path variable. Note that in modern Windows it shows a list of individual paths, the actual path variable is made by concatinating these paths together into one long string. Don't worry about that for now, all we need to do is click "New" and paste in the path to those `bin\` directories. We will add two new entries to this list.

![edit path](..\resources\edit-path.png)

Once those two new entries are added we are finished! Click "OK" and back out of these menus. The OS will now check both of these folders any time it is looking for a needed program or script. The last step would be to restart your PC so the changes take effect. 

**Get comfortable doing this, editing PATH is a very common step when installing development tools.**

## Configuring MongoDB with Auth
By default MongoDB does not run in authenticated mode, and will not require usernames or passwords when interacting with the databases. We need to change this right away. Now that we have mongosh installed, we can use it to manage MongoDB. In a new CMD window type `mongosh` to start the mongo shell.

### Add Administrator Account
By default MongoDB has already created several databases for you, including `admin`. Type the command `use admin` to switch to that database. You should see the prompt change to reflect the database in use. The prompt should now show `admin>_`. Use the following command to set up a root administrator:

```
db.createUser(
  {
    user: "<USERNAME>",
    pwd: "<PASSWORD>",
    roles: [ { role: 'root', db: 'admin' } ]
  }
)
```
You will need to edit this command to specify the username and password.

### Enable Auth Mode
Once your root admin user has been created we just need to turn on auth mode. We do so by editing the config file located in the MongoDB `bin\` folder. As a reminder, on Windows the default location is `C:\Program Files\MongoDB\Server\7.0\bin\`. You are looking for the file `mongod.cfg`, and you may need administrator privilages to edit this file. Open the file and look for the `security:` entry. It may be ignored, if you see a `#` symbol before `security:`, remove it. Finally, on the next line, add `  authorization: "enabled"`. When done it should look like this:

```
security:
  authorization: "enabled"
```
Note there are exactly two spaces at the beginning of that second line. Tab doesn't work here. Use the spacebar. You can copy/paste the entry as it is here right into your file.

After saving, restart your machine (or just the MongoDB service) and it will now be operating in auth mode.

