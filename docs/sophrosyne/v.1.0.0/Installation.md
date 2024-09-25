# Installation: Sophrosyne ©

Sophrosyne ©  supports currently Windows, Debian and Ubuntu based Installations

<table>
  <tr>
    <th>Windows</th>
    <th>Debian/Ubuntu</th>
        <th>Debian/Ubuntu (elevated rights)</th>
  </tr>
  <tr>
    <td style="text-align: center;"><img src="/sophrosyne/v.1.0.0/_media/WINDOWS_LOGO.png" alt="Windows Logo" style="width:100px"></td>
    <td style="text-align: center;"><img src="/sophrosyne/v.1.0.0/_media/DEBIAN_UBUNTU_LOGO.png" alt="Linux Logo" style="width:200px"></td>
    <td style="text-align: center;"><img src="/sophrosyne/v.1.0.0/_media/DEBIAN_UBUNTU_LOGO.png" alt="Linux Logo" style="width:200px"></td>
  </tr>
  <tr>
    <td style="text-align: center;"><a href="https://api.onedrive.com/v1.0/shares/u!aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBaUx4dFpNV2M3NTJ2Yjl6S2p5ZWhfcVpBenJzWkE_ZT1mblNCN3c/root/content">Download for Windows</a></td>
    <td style="text-align: center;"><a href="       https://api.onedrive.com/v1.0/shares/u!aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBaUx4dFpNV2M3NTJ2Yjl4TWdrNHBKcV9MbkdqU1E_ZT00YzFRQVc/root/content">Download for Debian/Ubuntu</a></td>
    <td style="text-align: center;"><a href="https://api.onedrive.com/v1.0/shares/u!aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBaUx4dFpNV2M3NTJ2Yjl5dVVOUnE2X1N0VXl4d0E_ZT16ODBCdUw/root/content">Download for Debian/Ubuntu</a></td>
    </tr>
    <tr>
    <td>
      <strong>SHA256 Checksum:</strong> 4d8b1f287e90066e8b4325c59595d84509a0e86666e1009ccb4fdde6cd2d3c73
    </td>
    <td>
      <strong>SHA256 Checksum:</strong> af2728b88f0616efbf7fe6c76f2300132012a4b280c0d9830364d024396ad87f
    </td>
    <td>
      <strong>SHA256 Checksum:</strong> 198ef23a20004e7364546ea876b748bf1f9df9225221a073906ed994e201f31d
    </td>
  </tr>
</table>

## Prerequisites Linux Installation

For Linux you have to additionally, make sure having postgres-16 installed.

The below installation script originates from the official [PGSQL Documentation](https://www.postgresql.org/download/linux/debian/)

```bash
# Create the file repository configuration:
sudo sh -c 'echo "deb https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

# Import the repository signing key:
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

# Update the package lists:
sudo apt-get update

# Install the latest version of PostgreSQL.
# If you want a specific version, use 'postgresql-12' or similar instead of 'postgresql':
sudo apt-get -y install postgresql-16
```

## Operations

Sophrosyne consists of 3 separate and decoupled services:

* Sophrosyne-Database Service running on <strong>Port: 61997</strong>
* Sophrosyne-Server Service running on <strong>Port: 17609</strong>
* Sophrosyne-UI Service running on <strong>Port: 27697</strong>

## Linux further Configuration

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

