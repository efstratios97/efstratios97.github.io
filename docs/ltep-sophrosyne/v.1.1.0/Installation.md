# Installation: LTEP Sophrosyne ©

Sophrosyne © V.1.1.0 supports currently Windows, Debian and Ubuntu based Installations

<table>
  <tr>
    <th>Windows</th>
    <th>Debian/Ubuntu</th>
  </tr>
  <tr>
    <td style="text-align: center;"><img src="/ltep-sophrosyne/v.1.1.0/_media/WINDOWS_LOGO.png" alt="Windows Logo" style="width:100px"></td>
    <td style="text-align: center;"><img src="/ltep-sophrosyne/v.1.1.0/_media/DEBIAN_UBUNTU_LOGO.png" alt="Linux Logo" style="width:200px"></td>
  </tr>
  <tr>
    <td style="text-align: center;"><a href="https://api.onedrive.com/v1.0/shares/u!aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBaUx4dFpNV2M3NTJ2WjFJbjNhbE9hemxzT2NSUkE_ZT1pbWZVcks/root/content">Download for Windows</a></td>
    <td style="text-align: center;"><a href="https://api.onedrive.com/v1.0/shares/u!aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBaUx4dFpNV2M3NTJ2WjFIZWZkM3lRMVhDOVpyNXc_ZT01ZlNpODQ/root/content">Download for Debian/Ubuntu</a></td>
    </tr>
    <tr>
    <td>
      <strong>SHA256 Checksum:</strong> 89004572BF91FEE54E6F114EFEC628FCFC2CCA28EA44BA9BD3E28E2DB759E84E
    </td>
    <td>
      <strong>SHA256 Checksum:</strong> 068FFD1A04E0A17FB2568D3E17C092300E75C9F5BA7CA7D40B1B5C3DEDAEFFB4
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
