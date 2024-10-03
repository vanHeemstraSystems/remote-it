# 300 - Building Our Application

## 100 - Getting Started with Remote.It in macOS Docker Desktop

MORE

## 200 - Connecting to Devices through Remote.It iOS App

On the iPad, download and install the Remote.It App.

Sign in with your Remote.It account.

Make sure the device (here: macOS Docker Desktop) has been registered and is connected with Remote.It. It will show up as **Docker Jumpbox** in the iPad App. It should list all containers of macOS Docker Desktop, now accessible through the iPad.

## 300 - Managing the Docker containers on Devices through a Command Line Interface (CLI) over the Internet

With a valid Remote.It registration key (e.g. XXXX-XXXX-XXXX-XXXXX-XXXX-XXXX-XXXX) you can open a terminal window from any computer connected to the Internet, with access allowed to ```remote.it```, and run following command to create a connection to such a device (here: macOS Docker Desktop):

```
$ docker run -d \
  -e R3_REGISTRATION_CODE="XXXX-XXXX-XXXX-XXXXX-XXXX-XXXX-XXXX" \
  -v /var/run/docker.sock:/var/run/docker.sock \
  --restart unless-stopped \
  --name remoteit_docker_jumpbox \
  remoteit/docker-extension:latest
```

The Docker container is synchronized with both the https://app.remote.it/#/devices/ web interface as well as the local-to-the-device actual docker container (here: macOS Docker Desktop on Willem's Mac Mini). 

**Note**: Make sure the port of the container (i.e. the service) is **Enabled**, otherwise the container can not be connected to. You can enable the service from the web interface, going to the particular container (e.g. ```Portainer (8000/tcp)```) and under the desired protocol (e.g. ```HTTPS```) tick the checkbox **Enable service**. In the web interface the button **> Connect** now becomes available. After having clicked the **> Connect** button, the upwards pointing arrow in the web interface or iOS App will reveal the public endpoint (e.g. ```3032be###################.p50.rt3.io```). Also htere is an arrow called **Launch** that lets you launch the Docker container for this service (e.g. port 8000). Click it to launch the container for that port.

## 400 - Remote.It Desktop

Alternatively or additionally you can download and install the Remote.It Desktop (for Linux, Windows, MacOS, etc).

See https://www.remote.it/download-list?products=desktop#Download-Results
It can be started, stopped, pauzed, and deleted using the standard docker commands from the terminal window thus controlling your docker containers remotely from where ever you are.
