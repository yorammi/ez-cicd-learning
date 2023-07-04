# Jenkins insatallation & setup
![ez logo](/resources/images/ez/ez-smiley-small-logo.png)
## setup Jenkins instance on Kubernetes
(based on the following page: https://octopus.com/blog/jenkins-helm-install-guide)

First, add the Jenkins repository to the local HELM catalog and update it:
```
helm repo add jenkins https://charts.jenkins.io
helm repo update
```
Then, deploy Jenkins instance:
```
helm upgrade --install myjenkins jenkins/jenkins
```
The output looks something like this:
```
Release "myjenkins" does not exist. Installing it now.
NAME: myjenkins
LAST DEPLOYED: Tue Oct 19 08:13:11 2021
NAMESPACE: default
STATUS: deployed
REVISION: 1
NOTES:
1. Get your 'admin' user password by running:
  kubectl exec --namespace default -it svc/myjenkins -c jenkins -- /bin/cat /run/secrets/chart-admin-password && echo
2. Get the Jenkins URL to visit by running these commands in the same shell:
  echo http://127.0.0.1:8080
  kubectl --namespace default port-forward svc/myjenkins 8080:8080

3. Login with the password from step 1 and the username: admin
4. Configure security realm and authorization strategy
5. Use Jenkins Configuration as Code by specifying configScripts in your values.yaml file, see documentation: http:///configuration-as-code and examples: https://github.com/jenkinsci/configuration-as-code-plugin/tree/master/demos

For more information on running Jenkins on Kubernetes, visit:
https://cloud.google.com/solutions/jenkins-on-container-engine

For more information about Jenkins Configuration as Code, visit:
https://jenkins.io/projects/jcasc/


NOTE: Consider using a custom image with pre-installed plugins
```
Now you can find out (and copy to your clipboard for your login needs) the 'admin' user password, by running the following command:
```
kubectl exec --namespace default -it svc/myjenkins -c jenkins -- /bin/cat /run/secrets/additional/chart-admin-password && echo
```
In order to check the login, you can run the following command:
```
kubectl --namespace default port-forward svc/myjenkins 8080:8080
```
The output should look like this:
```
Forwarding from 127.0.0.1:8080 -> 8080
Forwarding from [::1]:8080 -> 8080
```
and you can browse to:
```
http://localhost:8080
```
and login using the 'admin' user and the password you've saved, until you click:
```
Ctrl+C
```
in the terminal where you run the port-forward command.

To configure the Jenkins service as a LoadBalancer, you create a text file called 'values.yaml' with the following content:
```
controller:
  serviceType: LoadBalancer
```

One easy way to do it can be:
```
cat << EOF > values.yaml
controller:
  serviceType: LoadBalancer
EOF
```
You then upgrade the Helm release using the values defined in 'values.yaml' with with the command: 
```
helm upgrade --install -f values.yaml myjenkins jenkins/jenkins
```
The expected output show be:
```
Release "myjenkins" has been upgraded. Happy Helming!
NAME: myjenkins
LAST DEPLOYED: Tue Oct 19 08:45:23 2021
NAMESPACE: default
STATUS: deployed
REVISION: 4
NOTES:
1. Get your 'admin' user password by running:
  kubectl exec --namespace default -it svc/myjenkins -c jenkins -- /bin/cat /run/secrets/chart-admin-password && echo
2. Get the Jenkins URL to visit by running these commands in the same shell:
  NOTE: It may take a few minutes for the LoadBalancer IP to be available.
        You can watch the status of by running 'kubectl get svc --namespace default -w myjenkins'
  export SERVICE_IP=$(kubectl get svc --namespace default myjenkins --template "{{ range (index .status.loadBalancer.ingress 0) }}{{ . }}{{ end }}")
  echo http://$SERVICE_IP:8080/login

3. Login with the password from step 1 and the username: admin
4. Configure security realm and authorization strategy
5. Use Jenkins Configuration as Code by specifying configScripts in your values.yaml file, see documentation: http:///configuration-as-code and examples: https://github.com/jenkinsci/configuration-as-code-plugin/tree/master/demos

For more information on running Jenkins on Kubernetes, visit:
https://cloud.google.com/solutions/jenkins-on-container-engine

For more information about Jenkins Configuration as Code, visit:
https://jenkins.io/projects/jcasc/


NOTE: Consider using a custom image with pre-installed plugins
```
Run the following command to get the service's public IP address or hostname:
```
kubectl get svc --namespace default
```
And now you can browse to the Jenkins master server using that IP address or hostname:
```
http://service_ip_or_hostname:8080
```
