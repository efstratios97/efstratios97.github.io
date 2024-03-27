# Installation: LTEP Sophrosyne ©

Sophrosyne © v.1.2.0 supports currently Windows, Debian and Ubuntu based Installations

<table>
  <tr>
    <th>Windows</th>
    <th>Debian/Ubuntu</th>
  </tr>
  <tr>
    <td style="text-align: center;"><img src="/ltep-sophrosyne/v.1.2.0/_media/WINDOWS_LOGO.png" alt="Windows Logo" style="width:100px"></td>
    <td style="text-align: center;"><img src="/ltep-sophrosyne/v.1.2.0/_media/DEBIAN_UBUNTU_LOGO.png" alt="Linux Logo" style="width:200px"></td>
  </tr>
  <tr>
    <td style="text-align: center;"><a href="https://api.onedrive.com/v1.0/shares/u!aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBaUx4dFpNV2M3NTJ2WjE4aW5aYTI2eXdFVXo1WGc_ZT0wSDFqbFc/root/content">Download for Windows</a></td>
    <td style="text-align: center;"><a href="https://api.onedrive.com/v1.0/shares/u!aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBaUx4dFpNV2M3NTJ2WjE3a2VrTXBYUll3RVQ5WXc_ZT0xRFFBQ2U/root/content">Download for Debian/Ubuntu</a></td>
    </tr>
    <tr>
    <td>
      <strong>SHA256 Checksum:</strong> 50AA2A77FD988450FED123BCC915A2927B91FB0EE77FF92300634700783661C0
    </td>
    <td>
      <strong>SHA256 Checksum:</strong> 3D3C379B0C167B29E255B626109AFB62B521C96D947C4F58E33E39B4E4C08AA8
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

Sophrosyne consists of 3 seperate and decoupled services:

* Sophrosyne-Database Service running on <strong>Port: 61997</strong>
* Sophrosyne-Server Service running on <strong>Port: 17609</strong>
* Sophrosyne-UI Service running on <strong>Port: 27697</strong>