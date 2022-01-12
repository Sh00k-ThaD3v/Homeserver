<h1 align="center"><strong>The Modern HomeServer</strong></h1>

***
<p align="center">
  <a href="Justification.md">Why A Selfhosted Homeserver?</a> |
  <a href="https://www.docker.com/resources/what-container">Intro to microservices</a> |
  <a href="Recommendations.md">Hardware Recommendations</a> |
  <a href="#">How To Get Started?</a>
</p>

***

<h3 align="center">&bull; <strong>A fast, very low-maintenance, energy efficient selfhosted cloud.</strong></h3>
<h3 align="center">&bull; <strong>Can be used for any selfhosted system (from home automation to password manager).</strong></h3>
<h3 align="center">&bull; <strong>Can also be deployed and run in the background on your HomePC/Workstation.</strong></h3>
<h3 align="center">&bull; <strong>Carefully selected hardware recommendations.</strong></h3>
<h3 align="center">&bull; <strong>Carefully selected Operating System and server tools.</strong></h3>
<h3 align="center">&bull; <strong>Preconfigured automatic nightly/monthly maintenance.</strong></h3>
<h3 align="center">&bull; <strong>Carefully selected services for file cloud, password manager, media downloads and more.</strong></h3>

<sub>Note: I had zero experience when I started and learned everything by googling, spending time on fora, reddit and in documentations and by hours and days of trial&error. I made lots of mistakes. Now, in case of disaster I will use the scripts in this repository myself to get up and running again. I am documenting this because I haven't found a single source online that provides _all necessary information_ to get up and running. Also, lot's of things have been carefully chosen after testing alternatives. You can save lots of time with this guide! :) [basic Linux commands](https://www.hostinger.com/tutorials/linux-commands).</sub>

***
Jan 11th 2021: I am updating this guide to support Manjaro (Arch based) Linux instead of Ubuntu. 
After working with Ubuntu for 2 years, I learned Manjaro has lots of advantages for normal users and for a home server. 
Expect lots of updates until end of January (my personal deadline to update & fully test everything). 
***

## Features
* A file cloud using: _**FileRun**_ - Access and share your files from everywhere, sync your devices and enjoy your photo albums from any device, anywhere in the world. Fast and secure!
* A fantastic password manager: _**VaultWarden**_ - a.k.a Bitwarden, the best password manager available. 
* Your own Office Online/Google Docs: _**OnlyOffice**_ - integrates nicely with FileRun. 
* Your own browser sync: _**Firefox Sync Server**_ - your history, passwords, form fill info etc no longer shared with 3rd parties and easy to sync from laptop to phone.
* A highly secured reverse web proxy to be able to use all these features via your own domain like https://my.domain.cloud. 
* Your own ad-filtering or parental filtering dns server: _**AdGuard Home**_ - no more ads on any device within your network and even on your phone when you leave the house.
* Your own very fast VPN: _**Wireguard**_ - Your own VPN server and easy management of clients. To access services you do not want to expose publicly online.
* Your own paper scanning and organizing system _**Paperless-ng**_ - helps you to automatically archive your household administration and access documents easily.
* Your own media center server _**JellyFin**_ - Watch your series and movies on any smart TV or device. Also when you leave the home via VPN.
* Automatically follow and retrieve your favourite tv shows and movies _**Sonarr Radarr Bazarr QBittorrent**_ Because nobody can pay for every streaming service just to watch the few shows or movies they like. 
* Pretty dashboards to monitor your server _**Grafana, Prometheus**_ - Not necessary, but handy and with notifications. 
* Your own homepage to quickly access each service in a single webpage _**Organzir**_ See preview here.
For more details per app, [see here](https://github.com/zilexa/Homeserver/blob/master/Applications-Overview.md). 

***

### Step 1 - Install operating system - consider the Manjaro Gnome Post-Install script
- I highly recommend Manjaro Linux.
This guide used to be Ubuntu-based. All my laptops/PCs and my parents systems ran Ubuntu Budgie. After 2 years I switched to Manjaro (Gnome edition) and it is a delight!
A much better **out-of-the-box experience**, more **user-friendly** (also for setting up a server!)  **lightweight**, **small footprint**, much better and up to date single source of **high quality documentation (Arch Wiki)** and **MUCH easier to install applications + keep up to date** than any Ubuntu system. Also, better out-of-the-box BTRFS support. For small, flexible homeservers and personal laptops I strongly believe BTRFS is the best filesystem. If you have more needs, look at XFS/ZFS. This guide will use BTRFS. 
- My [Manjaro Gnome Post-Install script](https://github.com/zilexa/manjaro-gnome-post-install) provides an even better out-of-the-box experience. It also explains how to install Manjaro, select BTRFS and run the post-install script. 
- Make sure your OS is installed with BTRFS (no swap file, you can better configure that yourself later) and up to date before continuing. 


### Step 2 - Prepare server and docker
Continue to [Docker & server setup](https://github.com/zilexa/Homeserver/tree/master/docker) and use the bash script to automatically or manually install essential tools, apply basic configuration + required stuff for optional docker services. Get up and running in minutes via Docker Compose: _**this is the unique part of this guide, a complete and carefully built Docker-Compose.yml file, easy to personalize via the .env file containing all variables.**_

### Step 3 - Prepare data and backup drives
[Prepare the drives](https://github.com/zilexa/Homeserver/tree/master/filesystem). I understand your goal, make sane choices for your drives.

### Step 2. Data Migration & Folder Structure
Move files to your server data pool and [create your folder structure](https://github.com/zilexa/Homeserver/tree/master/filesystem/folderstructure). Note my folder structure might not fit your needs. It's up to you to decide how to structure your data. 

### Step 4 - Configure your apps & services
The Docker guide (step 3) explains how to access your services. Configuring & using your services is not covered by this guide. 
The overview of Docker applications below will contain some foldable sections with hints. 
[Overview of Docker Apps](https://github.com/zilexa/Homeserver/blob/master/Applications-Overview.md) contains direct links to the documentation or homepage of each Docker app. 

### Step 5 - Configure & schedule Maintenance
Nightly [maintenance](https://github.com/zilexa/Homeserver/tree/master/maintenance-tasks) of your server such as cleanup, backup and disks protection tasks. 

### Step 6 - Configure & schedule Backups
Decide what will be your [Backup Strategy](https://github.com/zilexa/Homeserver/blob/master/backup-strategy/backupstrategy.md) and use the [Server Backup Guide](https://github.com/zilexa/Homeserver/tree/master/backup-strategy) to leverage the BTRFS filesystem to backup your @, @home, @docker subvolumes and your data subvolumes easily, while also having a timeline/timemachine snapshots of your data. 

