# Installation: Sophrosyne ©

Sophrosyne ©  supports currently Windows, Debian and Ubuntu based Installations

<table>
  <tr>
    <th>Debian/Ubuntu (amd64)</th>
  </tr>
  <tr>
    <td style="text-align: center;"><img src="/sophrosyne/v.1.0.0/_media/DEBIAN_UBUNTU_LOGO.png" alt="Linux Logo" style="width:200px"></td>
  </tr>
  <tr>
    <td style="text-align: center;"><a href="https://drive.google.com/uc?export=download&id=170cqcZlDV7MrFHamdgZRPUo9S4O52zSg">Download for Debian/Ubuntu</a></td>
    </tr>
    <tr>
  </tr>
</table>

## Prerequisites Linux Installation

For Linux you have to additionally, make sure having postgres installed.

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

## Linux further Configuration - Database

You can use the `sophrosyne-db-setup` to configure, manage and operate a postgresql instance for you. It will setup it according to the db section of the default `sophrosyne-operations.yml` config-file.

## Linux further Configuration - Permissions

Under Linux, Sophrosyne runs using the current user used for the installation. Therefore, Sophrosyne rights to execute Actions (Scripts, commands) depends on the user rights: if your user can execute your command, then also Sophrosyne can <-> if your user cannot execute the command, then also Sophrosyne will not.
If you get `permission denied` errors, please check if your user has enough rights.


### Adjust systemd file

To enable Sophrosyne to execute actions with elevated rights, you can adjust the systemd "sophrosyne-server.service" file.

1. Open 
```/etc/systemd/system/sophrosyne_server.service```

```text
...
[Service]
User=%u
...
```

1. Change ```User=%u``` to a user with elevated/adequate rights for your actions

```text
[Service]
User=root // Although not recommended to use root
```

3. Reload service

```systemctl daemon-reload```

```systemctl stop sophrosyne_server.service```

```systemctl start sophrosyne_server.service```
