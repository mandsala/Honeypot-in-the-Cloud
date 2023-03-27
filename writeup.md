# Honeypot in the Cloud

### MHN-Admin Deployment

I deployed MHN-Admin using Google Cloud Platform and it was fairly easy to set up. I first had to create an account with GCP in which I was entitled to $100 of free credit to pay for the resources to deploy the VMs, and then I had to install and familiarize with GCP SDK. GCP SDK is essentially Google Cloud’s own set of commands to use on a host machine’s CLI. This allows for efficient administration of the cloud. After initializing GCP SDK with my GCP account, the process afterwards was fairly smooth. I first set a couple sub-sequent firewall rules to prepare to deploy the MHN-Admin VM. I did this by creating an allow rule to accept traffic from ports 80, 3000, and 10000. I then created an instance on the cloud to deploy an Ubuntu VM running on version 18.04 (minimal). Finally, after establishing an SSH connection to the VM, I installed the necessary packages to run MHN, did some additional configurations, and it was up and ready to have a honeypot linked to it. 

![honeypot1](https://user-images.githubusercontent.com/112013474/202011338-b8836a79-2b92-432c-b131-888722aeef39.gif)

### Dionaea Honeypot Deployment

What does Dionaea do?

Dionaea is what would be called a low-interaction honeypot as it emulates vulnerable resources openly to attackers in an attempt to capture information on the malware used to attack the system. 

![honeypot2](https://user-images.githubusercontent.com/112013474/202011488-9de4b815-e1aa-4cb5-a95e-38b712923733.gif)


### Database Backup

**Summary:** What is the RDBMS that MHN-Admin uses?

Modern Honey Network is a centralized server for management and data collection of honeypots. MHN-Admin sends intrusion detection logs, and depending on the technology used along with the honeypot (Dionaea, Cowrie, Snort) information on the attack will be captured diversly. 

In our case, the Dionaea technology used along with our honeypot allowed us to capture information about the attacks used on our honeypot. Dionaea’s specialty is that it traps the various malware used to exploit the vulnerabilities of the services shown on our honeypot to the attackers. The exported JSON file will not only have information regarding what was attacked, the IP that attacked, but also what malware and exploits were used for the attack, along with hashes of the malware. 
