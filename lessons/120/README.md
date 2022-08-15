## Intro

create infra with terraform
remove default vpc (disable compute api)
open GCP console, shouw that I have VPC with subnets,

## Managing SSH keys in metadata

generate ssh key (skip passphrase, otherwise you need to enter passphrase evry time you need to login)

```bash
ssh-keygen -t rsa \
-f ~/.ssh/gcp-lesson-120 \
-C my-username \
-b 2048
```

 ### project wide






























## Managing SSH keys in metadata
  OpenLDAP
## SSH using gcloud compute ssh
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
