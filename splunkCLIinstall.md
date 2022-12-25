   > ### Installation via CLI

   Use the following below for debian based distros 
   ```
   apt-get upgrade
   apt-get update
   ```
   Use the following below for RHEL based distros
   ```
   sudo dnf update
   sudo dnf upgrade 
   ```

1) Go to the Splunk Site https://www.splunk.com/en_us/download/splunk-enterprise.html
2) Create an account
3) Select Linux, click "download now" on .tgz
4) click on "Download via Command Line (wget)" top right corner
   ```
   sudo wget -O splunk-9.0.3-dd0128b1f8cd-Linux-x86_64.tgz "https://download.splunk.com/products/splunk/releases/9.0.3/linux/splunk-9.0.3-dd0128b1f8cd-Linux-x86_64.tgz"
   ```
5) Navigate to /opt
   ```
   cd /opt
   ```
6) Extract it tarzip. 
   ```
   tar xvzf splunk-9.0.3-dd0128b1f8cd-Linux-x86_64.tgz
   ```
7) once extracted, run the service by issuing the following below and complete the questionaire
   ```
   /opt/splunk/bin/splunk start --accept-license
   ```
8) once above completed. check for service port by issuing the following below
   ```
   ss -ntlpu |grep splunk
   ```
9) If you are running Firewalld. Issue the following below.
   ```
   firewall-cmd --add-port=8000/tcp --permanent
   firewall-cmd --reload
   ```

   ## The following are additional commands below are to manage (restart, stop & status) the splunk daemon.
   ```
   /opt/splunk/bin/./splunk restart
   /opt/splunk/bin/./splunk stop
   /opt/splunk/bin/./splunk status
   ```
