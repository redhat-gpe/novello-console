How to create a new lab console, example:

* Edit `openshift/sa.yaml` to add the new link
* Run: `oc project labconsole`
* Run: `oc replace -f openshift/sa.yaml`
* Run: `oc process -f openshift/labconsole.yaml   -p NAME=blue -p OS_AUTH_URL=http://169.47.17.15:5000//v3 -p OS_PROJECT_NAME=admin -p OS_USERNAME=admin -p OS_PASSWORD=PASSWORD | oc  create -f -`
* Scale to 5 (or 10 if is heavily used): `oc scale dc/blue  --replicas=5`

Example with blue, access to: `https://blue-labconsole.apps.shared.na.openshift.opentlc.com/`

---

Using helm chart:

- Create new project: `labconsole`
- Run:`helm install --set cloudauth.password='dummy' --set cloudauth.url='dummy' --set cloudauth.username='admin' --set  cloudauth.project='admin' helm-1 helm/`
- If you want to use different secret and handle on the fly run: `helm install --set cloudauth.secretName='osp-secret' --set cloudauth.secretEnable='false' --set handle='dynamicv2' labconsole-v1 helm/` 
  
  
