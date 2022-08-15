# OS Login + two factor + audit

https://cloud.google.com/compute/docs/oslogin/set-up-oslogin

grant permissions to user
with service account

show with and whiout service account to attach to the VM
For users that are outside of your organization

gcloud logging read --project=lesson-120 --freshness=1h 'protoPayload.serviceName="oslogin.googleapis.com"'

gcloud logging read --project=lesson-120 --freshness=1h 'protoPayload.serviceName="google.cloud.oslogin.v1.OsLoginService.CheckPolicy"'

How log commands executed by user









## From UI/browser