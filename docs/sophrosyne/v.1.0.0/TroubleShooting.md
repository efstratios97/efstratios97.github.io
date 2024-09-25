# Troubleshooting & Tips & Tricks

Find helpful information to make the most out of your experience with Sophrosyne

## Creating Windows Actions

<div style="background-color: #fff3cd; border: 1px solid #ffeeba; color: #856404; padding: 10px; margin-bottom: 15px; border-radius: 5px;">
  <b>For Windows Users</b><br/>
  <p>If your command is not in the path but callable via Window's cmd-prompt, you have to prepend (Respectively, for powershell or other services) <p style="font-family: monospace; background-color: #f0f0f0; padding: 5px; border-radius: 3px; border: 1px solid #ccc; overflow-x: auto;">cmd.exe /c</p></p>
  <p>Example using Windows Subsystem for Linux (WSL)</p>
  <p style="font-family: monospace; background-color: #f0f0f0; padding: 5px; border-radius: 3px; border: 1px solid #ccc; overflow-x: auto;">cmd.exe /c wsl ansible-playbook -i inventory.ini myAwesomePlaybook.yml</p>
</div>

## Creating Linux Actions

<div style="background-color: #fff3cd; border: 1px solid #ffeeba; color: #856404; padding: 10px; margin-bottom: 15px; border-radius: 5px;">
  <b>For Linux Users</b><br/>
  <p>If you execute scripts you have to prepend /bin/bash <p style="font-family: monospace; background-color: #f0f0f0; padding: 5px; border-radius: 3px; border: 1px solid #ccc; overflow-x: auto;">/bin/bash</p></p>
  <p>Example</p>
  <p style="font-family: monospace; background-color: #f0f0f0; padding: 5px; border-radius: 3px; border: 1px solid #ccc; overflow-x: auto;">/bin/bash /path/to/my/script.sh</p>
</div>

## Permission Settings / Denied (Linux)

<div style="background-color: #fff3cd; border: 1px solid #ffeeba; color: #856404; padding: 10px; margin-bottom: 15px; border-radius: 5px;">

Under Linux, Sophrosyne runs with the during installation auto-created user "sophrosyne". This user has no kind of elevated rights by default. When Actions are executed, they are done so with the restricted rights of the "sophrosyne" user, which will eventually result in permission denied errors. 


### Solution 1: Adjust systemd file

To enable Sophrosyne to execute actions with elevated rights, you can adjust the systemd "sophrosyne-server.service" file.

1. Open 
```/etc/systemd/system/sophrosyne_server.service```

```text
[Unit]
Description=Sophrosyne-Server
After=network.target

[Service]
Type=simple
User=sophrosyne
ExecStart=/usr/bin/sophrosyne/jre/bin/java -jar /usr/bin/sophrosyne/server/bin/sophrosyne.jar
ExecStop=/bin/kill -SIGINT $MAINPID
SuccessExitStatus=143

[Install]
WantedBy=multi-user.target
```

1. Change ```User=sophrosyne``` to a user with elevated/adequate rights for your actions

```text
[Unit]
Description=Sophrosyne-Server
After=network.target

[Service]
Type=simple
```
```User=root```
```text
ExecStart=/usr/bin/sophrosyne/jre/bin/java -jar /usr/bin/sophrosyne/server/bin/sophrosyne.jar
ExecStop=/bin/kill -SIGINT $MAINPID
SuccessExitStatus=143

[Install]
WantedBy=multi-user.target
```

3. Reload service

```systemctl daemon-reload```

```systemctl stop sophrosyne_server.service```

```systemctl start sophrosyne_server.service```

### Solution 2: Elevate rights

Give sophrosyne user elevated rights by adding it to sudoers

https://linuxize.com/post/how-to-add-user-to-sudoers-in-ubuntu/

### Solution 3: Change user permission of scripts and files

https://www.redhat.com/sysadmin/manage-permissions


</div>