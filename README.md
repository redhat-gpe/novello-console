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
- Create a secret in the new project with:
  - `osp_auth_url`
  - `osp_auth_password`
  - `osp_auth_username`
  - `osp_auth_password`
- Run: `helm install labconsole-v1 helm/`
- If you want to use different secret and handle on the fly run: `helm install --set buildconfig.env.secret='osp-secret' --set handle='dynamicv2' labconsole-v1 helm/` 
  
  
