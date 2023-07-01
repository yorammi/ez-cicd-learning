# ez-nexus-demo
![ez logo](/resources/images/ez/ez-logo-small.png)
# <font color=blue size="16">ez-nexus-demo</font>


## setup Nexus server

Setup Nexus server, by running:
```
mkdir ~/nexus-data && chmod -R 777 ~/nexus-data
docker run -d -p 8081:8081 --name nexus -v ~/nexus-data:/nexus-data sonatype/nexus3
```
Follow the server log until you see it is up and running:
```
docker logs -f nexus
```

Browse to the Nexus server:
```
http://<IP>:8081
```

To find out the initial password of the 'admin' user, run:
```
docker exec nexus cat /nexus-data/admin.password
```
Once you login, you will be asked to set the permanent 'admin' password.
