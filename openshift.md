# OpenShift

Ref:  https://www.youtube.com/watch?v=yFPYGeKwmpk

Diagram:  https://github.com/Skatteetaten/aurora-openshift/blob/master/images/deploy.png

Openshift is RedHat's attempt to create a Platform as a Service stack including container launching, storage(?), cluster management/ routing and such...  It's similar to Dokku in that it is a PAAS that runs services by orchestrating containers to launch, but isn't easy to configure and in fact the central installation mechanism (a RedHat managed Ansible repository) goes through periods of in-operability and is poorly monitored by staff.  This is likely due to the fact that RedHat is marketing both RHEL which may install OpenShift better (though likely this will not be a very smooth process) as well as the fact that RHEL is marketing RedHat managed OpenShift cloud service.

Openshift is built ontop of Google's Kubernetes which makes me think that it would be ideal to just use Kubernetes to deploy microservices instead of using OpenShift.



###### Apps

Apps are broken down to the following hierarchy

  - Projects
    - Applications (an app)
      + Deployment Config/ Replication Controller (Management interface for a Cluster of Containers)
      + Pod (the cluster of containers based around a particular image)
      + Service (This is a loadbalance for a pod)
      + Routes
      + Image Stream
      + Config Map


###### Builds

You can have your app's source code built into an image automatically by OpenShift.  It's super snazzy but completely optional (some people prefer to build their source code within a Jenkins job).


###### Deployments (aka Deployment Configurations, aka replication controllers, aka microservices)

You can have one deployment of your code/ image scaled up to as many pods of CPU as you'd like!


## CLI Cheat Sheet

https://docs.openshift.com/enterprise/3.0/cli_reference/basic_cli_operations.html

-  Config file: `~/.kube/config`
- `oc types` - show a cheatsheet!

###### Account Stuff
- `oc login/logout` - authenticate
- `oc project PROJ_NAME` - switch to the project you'd like to work on
- `oc whoami`
- `oc status`

###### App Creation/ Deletion
- `oc new-app --docker-image=blah --name=app-name --allow-missing-images --labels=app-name`
- `oc delete all -l app=$PAAS_APP` - Delete an entire micro-service dealy based on your tagging strategy
- `oc delete dc APP_NAME` - Delete a Deployment Configuration by it's name

###### Resource Monitoring
- `oc get all` - Get a list of all the resources that have been created in OpenShift
- `oc get all -l app=$PAAS_APP` - Filter by the built-in tag 'app'
- `oc describe <RESOURCE>` - Get detailed information about a resource
- `oc get dc` - list deployment configurations (aka microservices)

###### App Monitoring/ Debugging
- `oc logs dc/$PAAS_APP`
- `oc rsh POD_ID`

## Creating a Service Account

```
namespace=test

oc create serviceaccount robot
oc policy add-role-to-user view system:serviceaccount:${namespace}:robot
oc policy add-role-to-user admin system:serviceaccounts:${namespace}:robot
oc serviceaccounts get-token robot
```

You can list the users/ roles with `oc get rolebindings`.

###### Service Acc usage

```
token=$(oc serviceaccounts get-token robot)
namespace=test

curl -X GET -H "Authorization: Bearer ${token}" "https://example.com/api/v1/namespaces/${namespace}/configmaps" --insecure
```





## On Debugging...

`oc` with `--loglevel=6` (or higher) is useful for figuring out those API calls.


## Templates and Jazz


The things in the OpenShift catalog are called "templates" and they are just a bunch of appended yaml with some variables injected.  You can write your own.

  https://github.com/openshift/library/blob/master/official/rails/templates/rails-postgresql-example.json

You can search for available templates on the CLI  with: `oc new-app -S --template=rails`



Export your existing deploymentconfig via this command...

```
oc export dc -l app=myapp-stage --as-template="myapp-head" > ose3/openshift_deployment.yml
```



















## Setup a Friggin Micro-Service

```
export DOCKER_IMAGE='phocean/etherpad:latest'
export PAAS_APP='etherpad-poc'

# Make a bunch of resources for the micro-service to exist...
# specifically:  imagestreamtag, deploymentconfig, services
oc new-app --docker-image=$DOCKER_IMAGE \
           --name=$PAAS_APP \
           --allow-missing-images

oc expose svc $PAAS_APP \
   || oc expose dc/$PAAS_APP --port=8080
```


Okay, once you run those commands the first time, you'll have created the app.  When you're ready to begin rolling out a new version, you'll want to run this command:

```
oc rollout latest $PAAS_APP
```

If you want to deploy an image other than latest, change that part of the command, and you'll be all set :D


###### Use a template when rolling out a new deployment
```
oc rollout latest myapp-stage --template=jenkinsfiles/openshift_deployment.yml
```



Also see openshift.secret.md!


