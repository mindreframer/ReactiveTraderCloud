# Docker Issues

You will find here some of the common issues we had with docker.

# LINUX
### UBUNTU
Docker can complain of not having `permissions`. So the first reflex is to run everything as `sudo`.  
But the real reason is that you need to be in the docker group in order to run docker commands.

To achieve that, just run
- `$ sudo gpasswd -a ${USER} docker`
- logout and login

# MAC

### repository must be in Users folder

The different scripts here will need to share code with the different containers. On Windows and Mac, the sharing is between the container and the virtual machine. The virtual machine is defined to share your home folder (/c/Users/ for windows or /Users for mac). If your git clone folder is a children folder of your home user, it's fine. Else you need to open VirtualBox and share that specific folder.

### no space left on device
```
Error pulling image (0.0) from docker.io/reactivetrader/servers, 
endpoint: https://registry-1.docker.io/v1/, 
Untar re-exec error: 
exit status 1: 
output: 
write /usr/share/mime/packages/freedesktop.org.xml: 
no space left on device
```

try to stop and restart the docker virtual machine:
```bash
docker-machine stop default
docker-machine start default
```
Then close the `Docker Quick Start Terminal` and open a new once.

If the issue persist, try to remove the virtual machine and generate a new one:  
- open virtualbox Gui
- right click on the `default` machine and remove it with all its files
- close virtualbox Gui
- open a new docker Quick Start Terminal
- wait for the new VirtualMachine to be generated

# WINDOWS

### repository must be in Users folder

The different scripts here will need to share code with the different containers. On Windows and Mac, the sharing is between the container and the virtual machine. The virtual machine is defined to share your home folder (/c/Users/ for windows or /Users for mac). If your git clone folder is a children folder of your home user, it's fine. Else you need to open VirtualBox and share that specific folder.