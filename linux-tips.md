Linux Tips
====
This is a collection of the commands and items that might prove useful.

Remember, `apt` is designed for more of a user-friendly version of `apt-get`.


OS Setup
-----

### Update & Maintain the Distro

`sudo apt-get update && sudo apt-get dist-upgrade`

### Installing .deb Files

Ubuntu by itself locks down .deb files.  We will use gdebi to install .deb files.

`sudo apt-get install gdebi`

`sudo gdebi installFile.deb`

### Install File Compression Libraries

`sudo apt-get install unace unrar zip unzip xz-utils p7zip-full p7zip-rar sharutils rar uudeview mpack arj cabextract file-roller`

### Install Ubuntu Restricted Extras
`sudo apt install ubuntu-restricted-extras`


Skype Installation
----

1. Navigate to where you can download. e.g., `cd ~/Downloads`
2. Download Skype: `wget https://go.skype.com/skypeforlinux64-deb`
3. Install Skype:  `sudo gdebi ./skypeforlinux64.deb`

Java Installation
----

### Ensure OpenJDK is Uninstalled
1. `dpkg -l | grep openjdk`
2. `dpkg -l | grep jre`

If there is presence of OpenJDK, remove it:

1. `sudo apt-get --purge remove openjdk*`
2. `sudo apt-get autoremove`

### Install Java 8
1. `sudo add-apt-repository ppa:webupd8team/java`
2. `sudo apt-get update`
3. `sudo apt-get install oracle-java8-installer`

### Install Alternatives for easy Java Switching
* `sudo apt install galternatives`

Installing Git and Repos
----

### Install Git & Other Necessary Tools
`sudo apt update && sudo apt install git xclip`

### Generate an SSH Key
`ssh-keygen -t rsa -b 4096 -C "github@email.com"`

### Adding the SSH Key to Github
1. `eval "$(ssh-agent -s"`
2. `ssh-add ~/.ssh/id_rsa`
3. `xclip -sel clip < ~/.ssh/id_rsa.pub`

### Clone the Repo
1) Navigate to where you want the repo.
2) `git clone git@github.com:projectName/branch.git`

MySQL Sandbox Installation
----

### Setup MySQL Sandbox
`sudo apt install mysql-sandbox libaio1 libaio-dev`

### Setup MySQL Sandbox Variables
1) Edit the bash profile: `sudo nano ~/.bashrc`
2) Add in the Environment Variables:

(This is where the MySQL servers are installed into.)
* `export SANDBOX_HOME=/home/usernamehere/Liferay/MySQL/servers`

(This is where the MySQL Installation (tar.gz) Files go.)
* `export SANDBOX_BINARY=/home/usernamehere/Liferay/MySQL/tarballs`

### Setup MySQL Sandbox Defaults
`sudo nano /usr/share/perl5/MySQL/Sandbox.pm`
Edit the default_users section:
* `db_user = root`
* `db_password = password`
* `remote_access = %` 
This allows all remote connections.

### Setup UTF-8 Compatibility
1) Edit the `my.sandbox.cnf` file in each of the MySQL servers.
2) Place the following properties under the `[mysqld]` section.
```
[mysqld]
character-set-server=utf8
collation-server=utf8_general_ci
```

### Install MySQL Workbench
`sudo apt install mysql-workbench`

### Using MySQL Sandbox
* `./start` in the server folder to start up the server.
* `./stop` to stop the server.
* `./my sql` calls up the MySQL prompt.
* `./my sqldump` to call the MySQL dump command.

**NOTE:** You call commands like mysqldump, etc. by just the use of something like `./my sqldump`

VMware Player
----
### Installing VMware Player
* `sudo apt update`
* `wget https://download3.vmware.com/software/player/file/VMware-Player-14.1.1-7528167.x86_64.bundle`
* `chmod a+x ./VMware-Player-14.1.1-7528167.x86_64.bundle`
* `sudo ./VMware-Player-14.1.1-7528167.x86_64.bundle`

Setting Up Aliases, Functions, and Environment Variables
----
The `.bashrc` file is where you can set aliases, functions, and environment variables to be used within Linux.

### Editing the File
`sudo nano ~/.bashrc`

### Example Aliases
* `alias clr='clear'`
* `alias navd='cd ~'`
* `alias gm='git merge'`

### Example Functions
```
function() lrclean{
rm -rf ./osgi/state/*
rm -rf ./temp/*
rm -rf ./work/*
}
```

### Example Environment Variables
`export ANT_OPTS="-Xms256m -Xmx4g"`
