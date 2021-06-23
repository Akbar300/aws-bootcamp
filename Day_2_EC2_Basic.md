# Day 2 EC2 Basic 

# Quick `VPC` Intro

- Virtual Private Cloud 
- Default VPC , Subnets in each AZ
  - us-east-1 has 6 AZs and one Subnets under each AZ  
- EC2 is created under Availibility zone in VPC subnets
- A lot of networking configuration has already been done for you so you can get started easily without much of networking set up
---

# EC2 : Elastic Computing Cloud 
- IaaS in AWS 
- Virtual Machines in the cloud - instances
- Private by default unless made public
- Launched in certain AZ(availibility zone)
- Different sizes and capability 
- On Demand billing - per second or hour
- Launched on EC2 host (actual hardware) 
  - multiple ec2 instances share same hardware 
  - Shared Host  VS Dedicated host
- Instance Lifecycle 
  - Running 
  - Stopped 
  - Terminated
---
## `AMI` : Amazom Machine Image 
- Snapshot of pre-configured EC2 instance with operating system (optionally some software on it)
- Permission Can be public or private 
---

## Creating EC2 instance 
Navigate to EC2 console and Click launch instance
 1. Select AMI (linux or windows)
 2. Select insatance size (t2 micro)
 3. Optionally Select VPC-Subnets (alrady set by default)
    1. Optionally Add user data script to run after launch
 4. Optionally Add or change Storage
 5. Optionally Add tags
 6. Select or Create Security Group (virtual firewall)
 7. Review and Launch
---

## Creating EC2 using `Launch Template`
You can create a template with pre-configured selections to quickly launch instances or later attach it to a autoscaling groups


## Optionally Creating Elastic IP Address
- EC2 instance public IP is dynamic and changed everytime the machine is stopped and restarted.
- Elastic IP can be allocated and attched to an EC2 insatnce at a time to ensure static IP address 
- It can be reassigned to different instances if needed.
- Free while attacthed to a running instance

## Connecting to EC2 
- Linux :  
  - Most of the them does not have UI , will use command line commands to interact.
  - `SSH` (secure shell protocol)
    EC2 ssh Keypair with public and private key , public key will be in ec2 , private key will be on connecting machine. 
    port 22 is used  
  - Mac comes with SSH built in 
  - Windows can use PuTTY

> Easy way to connect to Linux shell environment is is using `EC2 Instance connect` from AWS Console

- Windows : 
  - `RDP` (Remote Desktop Protocol)
    > RDP come with windows no extra software needed while connecting from windows machine 
  - [Download RDP software](https://apps.apple.com/us/app/microsoft-remote-desktop/id1295203466?mt=12) if you are connecting from windows



### Linux User Data script to 
- Install and run simple http server to serve html files


```bash
#!/bin/bash
 
sudo yum update -y
# Install http server
sudo yum install httpd -y
# Start HTTP server
sudo service httpd start
sudo chkconfig httpd on
# Add Simple index.html file into under desired location
echo "<html><body><h1>Hello Cybertek Alumni, this is web server
1</h1></body></html>" > /var/www/html/index.html
```


### Linux User Data script to 
  - install docker with required permissions 
  - install docker-compose
  - download sample docker compose file
  - install git
  - reboot to get script to take affect 

```bash
#!/bin/bash
sudo yum update -y && sudo amazon-linux-extras install -y docker && sudo service docker start && sudo usermod -a -G docker ec2-user && sudo chkconfig docker on && sudo yum install -y git && sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose && docker-compose version && sudo curl -L https://cybertek-shared.s3.amazonaws.com/docker-compose.yml -o /home/ec2-user/docker-compose.yml && sudo reboot
```


### Windows User Data script to 
  - Set Default shell location
  - Change TimeZone
  - install Crhome on Windows with PowerShell
  - Set Chrome as default browser

```powershell
<powershell>
Set-Location "C:\Windows\system32"

#Change TimeZone
C:\Windows\System32\tzutil /s "Eastern Standard Time"

#Install Chrome 
$Path = $env:TEMP;
$Installer = "chrome_installer.exe";
Invoke-WebRequest "http://dl.google.com/chrome/install/375.126/chrome_installer.exe" -OutFile     $Path\$Installer; 
Start-Process -FilePath $Path\$Installer -ArgumentList "/silent /install" -Verb RunAs -Wait;
Remove-Item $Path\$Installer

#Set Chrome as default browser
$chromePath = "${Env:ProgramFiles(x86)}\Google\Chrome\Application\" 
$chromeApp = "chrome.exe"
$chromeCommandArgs = "--make-default-browser"
& "$chromePath$chromeApp" $chromeCommandArgs

</powershell>
```
