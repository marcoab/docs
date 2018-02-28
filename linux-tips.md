Linux Tips
====
This is a collection of the commands and items that might prove useful.

Remember, `apt` is designed for more of a user-friendly version of `apt-get` !


OS Setup
-----

### Update & Maintain the Distro

`sudo apt-get update && sudo apt-get dist-upgrade`

### Installing .deb Files

Ubuntu by itself locks down .deb files.  We will use gdebi to install .deb files.

`sudo apt-get install gdebi`

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
* `dpkg -l | grep openjdk`
* `dpkg -l | grep jre`
* If there is presence of OpenJDK, remove it:
* `sudo apt-get --purge remove openjdk*`
* `sudo apt-get autoremove`

### Install Java 8
1. `sudo add-apt-repository ppa:webupd8team/java`
2. `sudo apt-get update`
3. `sudo apt-get install oracle-java8-installer`



