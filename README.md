# 🛡️ Wazuh Server Installation Guide on Ubuntu (Manager Setup)

This guide walks you through installing the Wazuh security monitoring platform on Ubuntu (running in VirtualBox) as a manager (server). It includes setting up agents and securing communication between them.

## 🚀 Prerequisites

- Ubuntu installed in VirtualBox  
- Internet access  
- Basic terminal experience  
- Browser (e.g., Firefox) to access the dashboard  

## 🧰 Installation Steps

Wazuh server installation guide on ubuntu as the manager
1. Install ubuntu to vbox
2. sudo apt update && sudo apt upgrade -y
3. sudo apt install curl
4. sudo apt install default-jdk -y
5. https://documentation.wazuh.com/current/installation-guide/wazuh-server/installation-assistant.html
6. curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh 
7. bash wazuh-install.sh -a
8. You will provided a username and password 
9. Navigate to firefox and access <https://ubuntu-ip:443> 

To change the password because wazuh won't allow you to change it on the dashboard
 cd /var/ossec/bin
 bash wazuh-passwords-tool.sh -u <username> -p (new password)
 Go back to wazuh and reload

To deploy an agent from the dashboard from (ubuntu)
Go to <https://ubuntu-ip:443> and deploy new agent
1. Linux, windows, macOs
2. Server address (ubuntu ip)
3. Agent name (optional)
4. Copy the command in step 4(wazuh dashboartd) and paste it on your agent terminal(windows will be ran on powershell)
5. Add agent(kali) to manager
 - sudo /var/ossec/bin/manage_agents

 - Press A to add new agent

 - Enter agent name, IP (optional)

 - Get the key and copy it
6. Import key on agent - sudo /var/ossec/bin/manage_agents
 - Choose I to import keys, save and exit

 - sudo tail -f /var/ossec/logs/ossec.log to confirm if agent is connected to the manager

7. Log in to wazuh dashboard and refresh. An agent should be included
