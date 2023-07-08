# EZ! ArgoCD challange
![ez logo](/resources/images/ez/ez-smiley-small-logo.png)
## ArgoCD installtion

See: [ArgoCD installation](/learning-workspace-setup/argocd-installation.md)

## ArgoCD test application setup

Open a browser to the Argo CD external UI

![ArgoCD login](/resources/images/argocd/argocd-login.png)

Login by visiting the IP/hostname in a browser

![ArgoCD after login](/resources/images/argocd/argocd-after-login.png)

After logging in, click the + New App button as shown below:

![ArgoCD after login](/resources/images/argocd/argocd-new-app.png)

The following form will popup:

![ArgoCD new app form](/resources/images/argocd/argocd-new-app-form.png)

In the form, in the ```GENERAL``` section, you should provide the following values for the fields:

- Application Name: ```guestbook```
- Project: ```default``` (selected from the dropdown list)
- SYNC POLICY: ```Manual``` (leave the default value)

In the ```SOURCE``` section, provide the following values:

- Repository URL: ```https://github.com/yorammi/ez-argocd-example-apps.git```
- Revision: ```HEAD```
- Path: ```guestbook```

IN the ```DESTINATION``` section, provide those values:

- Cluster: ```https://kubernetes.default.svc```  (or cluster name)
- Namespace: ```default``` 

After filling out the information above, click Create at the top of the UI to create the ```guestbook``` application:

![ArgoCD create app](/resources/images/argocd/argocd-create-app.png)

Now you'll see the application list, including the following ```guestbook``` app.

![ArgoCD APPs list](/resources/images/argocd/argocd-guessbook.png)

First you should click the ```SYNC``` button, in order to start syncing, and the click the name of the app, or anywhere inside the app details, in order to see the ```APPLICATION DETAILS TREE```

![ArgoCD APPLICATION DETAILS TREE](/resources/images/argocd/argocd-guessbook-details-tree.png)

