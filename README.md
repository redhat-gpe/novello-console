How to create a new lab console, example:

* Edit `openshift/sa.yaml` to add the new link
* Run: `oc project labconsole`
* Run: `oc replace -f openshift/sa.yaml`
* Run: `oc process -f openshift/labconsole.yaml   -p NAME=blue -p OS_AUTH_URL=http://169.47.17.15:5000//v3 -p OS_PROJECT_NAME=admin -p OS_USERNAME=admin -p OS_PASSWORD=PASSWORD | oc  create -f -`

Example with blue, access to: `https://blue-labconsole.apps.shared.na.openshift.opentlc.com/`
