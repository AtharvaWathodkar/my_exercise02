- show how to add custom ssh key to the ssh client ssh-add
- connect with LDAP

- ssh to private instances

gcloud compute ssh INTERNAL_INSTANCE_NAME \
    --zone=ZONE \
    --internal-ip




## Create SSH keys





1. project wide (how to quesry metadata from the server)

Firewall: allow-ssh

curl http://metadata.google.internal/computeMetadata/v1/project/attributes/ssh-keys \
-H "Metadata-Flavor: Google"

delete VM and the public key from gcp project

2. add ssh key during creation of vm



curl http://metadata.google.internal/computeMetadata/v1/instance/attributes/ssh-keys \
-H "Metadata-Flavor: Google"



(remove public/private google ssh keys) (show empty ssh keys in google concole)
gcloud compute ssh instance-1 \
    --project=lesson-120 \
    --zone=us-central1-a \
    --internal-ip







## --tunnel-through-iap (with permissions) only for private
https://cloud.google.com/iap/docs/tcp-forwarding-overview
https://cloud.google.com/iap/docs/using-tcp-forwarding

Tunnel the ssh connection through Cloud Identity-Aware Proxy for TCP
          forwarding.

Create a firewall rule
applies to all VM instances that you want to be accessible by using IAP.
allows ingress traffic from the IP range `35.235.240.0/20`. This range contains all IP addresses that IAP uses for TCP forwarding.
allows connections to all ports that you want to be accessible by using IAP TCP forwarding, for example, port `22` for SSH and port 3389 for RDP.

If the instance doesn't have an external IP address, the connection automatically uses IAP TCP tunneling. If the instance does have an external IP address, the connection uses the external IP address instead of IAP TCP tunneling.
You can use the --tunnel-through-iap flag so that gcloud compute ssh always uses IAP TCP tunneling.

gcloud compute ssh private-instance \
    --project=lesson-120 \
    --zone=us-central1-a \
    --tunnel-through-iap

gcloud compute ssh instance-1 --project=lesson-120 --zone=us-central1-a --troubleshoot --tunnel-


try to connect to public instance using `gcloud compute ssh instance-1` and get timeout since it will use public ip

gcloud compute ssh public-instance \
    --project=lesson-120 \
    --zone=us-central1-a


## show what happens if block project wide keys happen (Updating instance ssh metadata)

## copy something to vm using scp

gcloud compute scp --recurse \
example/nginx private-instance-block:~/example \
--project=lesson-120 \
--zone=us-central1-a \
--tunnel-through-iap