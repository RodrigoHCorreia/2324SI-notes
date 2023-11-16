# Load balancers, services, ctl, demons, shell script etc.

## Work diagram 

![work-diagram-phase-3](<WhatsApp Image 2023-11-09 at 10.09.07_689a539b.jpg>)

**systemctl** is the command to manage systemd.
sudo systemctl isolate multi-user.target - changes the runlevel to multi-user.target
the default runlevel is graphical.target (GUI)

## Service

A service is a unit file that describes a process that should be managed by systemd.

```bash
#! /bin/bash 

echo "This is a useless service."

while :
do
    sleep 5
    echo "Still a useless service..."
done
```

in order to make this a service we need to integrate this.
in ls /lib/systemd/system we can see all the services that are running.

in order to reconfigure or add a new service we need to change it in a different directory, /etc/systemd/system.

```bash
[Unit]
Description=A very useless service.

[Service]
ExecStart=path/to/useless.sh
Restart=always
User=isel #This will run the service as the isel user instead of root, making it's permissions more restricted.
Group=isel
```

**systemctl daemon-reload** - reloads the unit files in /etc/systemd/system

**systemctl status useless** - shows the status of the service

**sudo systemctl start useless** - starts the service

**sudo systemctl stop useless** - stops the service (faz um pedido educado (sigterm) para o processo terminar)

**journalctl -u useless** - shows the logs of the service (-u is for unit)

We can avoid the sigterm by changing the script

```bash
#! /bin/bash 

echo "This is a useless service."

function handleTerm {
    echo "I refuse to stop being a useless service."
}

trap handleTerm SIGTERM
while :
do
    sleep 5
    echo "Still a useless service..."
done
```

To create a link we use ln -s /path/to/file /path/to/link
To make a script executable we use chmod +x /path/to/file

## Reload vs Restart

**Reload**d doesn't restart the service, it just reloads the unit file with the new configuration. 
**Restart** will shut down the service and start it again.