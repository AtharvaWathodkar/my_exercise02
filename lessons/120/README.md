## Intro

create infra with terraform
open GCP console, show default VPC and firewalls
open GCP console, shouw that I have VPC with subnets
remove default vpc (disable compute api)

## Managing SSH keys in metadata

generate ssh key (skip passphrase, otherwise you need to enter passphrase evry time you need to login)

can be rsa or eliptic curve

```bash
ssh-keygen -t rsa \
-f ~/.ssh/gcp-lesson-120 \
-C my-username \
-b 2048
```

### project wide

upload ssh key to the project metadata

create VM in public subnet with public ip
Name: public-instance-1
Region: us-central1
Machine: e2-micro
Networking:
  Subnetworking: public
  Externla: ephemeral

Try to SSH to the instance using public IP and get timeout

```bash
ssh -i ~/.ssh/gcp-lesson-120 my-username@35.225.171.136
```

ssh: connect to host 35.225.171.136 port 22: Operation timed out

open firewall
Name: allow-ssh
Network: main
Targets: all instances
Source: 0.0.0.0/0
Ports: tcp 22

Try to SSH again (success)

```bash
ssh -i ~/.ssh/gcp-lesson-120 my-username@35.225.171.136
```

if you use ssh agent you can add private key
add private key to the ssh agent

ssh-add ~/.ssh/gcp-lesson-120

Try again

ssh -i ~/.ssh/gcp-lesson-120 my-username@35.225.171.136


delete the SSH key from the project

### add ssh key to VM

create VM in public subnet with public ip
Name: public-instance-2
Region: us-central1
Machine: e2-micro
Networking:
  Subnetworking: public
  Externla: ephemeral
Security:
  Add Key: 

show how to add SSH key when VM is already created

try to ssh to VM

ssh -i ~/.ssh/gcp-lesson-120 my-username@35.225.171.136




















## Managing SSH keys in metadata
  OpenLDAP
## SSH using gcloud compute ssh Identity-Aware Proxy (IAP) for TCP
## OS Login
## Audit Logs


















How To SSH into your VM? - Google Cloud Platform (GCP | 5 Ways | OS Login | SSH metadata)

start from clean slave

About SSH connections
https://cloud.google.com/compute/docs/instances/ssh

Connect to Linux VMs using Google tools
https://cloud.google.com/compute/docs/instances/connecting-to-instance

Choose an access method
https://cloud.google.com/compute/docs/instances/access-overview?_ga=2.59588269.-1034640511.1643984674

- OS Login (Preffered, should be last item in the list) https://cloud.google.com/compute/docs/oslogin#benefits_of_os_login
  - two-factor
  - but not the ability to run commands such as sudo
  - what else i can restrict
  - Automatic permission updates
  - Ability to import existing Linux accounts
  - Monitor OS Login audit logs 
- Managing SSH keys in metadata
  - Active Directory
  - LDAP
- Temporarily grant a user access to an instance


transfer files to and from VM

- delete default network
- show empty firewalls
- with graphics from photoshop



## Public SSH
- block project wide SSH keys


## OS Login



https://cloud.google.com/sdk/gcloud/reference/compute/ssh
https://kloudle.com/academy/5-ways-to-connect-to-your-gcp-vm-instances-using-ssh

Opening in browser window


gcloud compute firewall-rules create \
--project=lesson-120 \
--network=main \
--allow=tcp:22 \
default-allow-ssh
