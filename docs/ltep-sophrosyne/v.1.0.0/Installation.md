# Installation: LTEP Sophrosyne ©

Sophrosyne © V.1.0.0 supports currently Windows, Debian and Ubuntu based Installations

<table>
  <tr>
    <th>Windows</th>
    <th>Debian/Ubuntu</th>
  </tr>
  <tr>
    <td style="text-align: center;"><img src="/ltep-sophrosyne/v.1.0.0/_media/WINDOWS_LOGO.png" alt="Windows Logo" style="width:100px"></td>
    <td style="text-align: center;"><img src="/ltep-sophrosyne/v.1.0.0/_media/DEBIAN_UBUNTU_LOGO.png" alt="Linux Logo" style="width:200px"></td>
  </tr>
  <tr>
    <td style="text-align: center;"><a href="https://api.onedrive.com/v1.0/shares/u!aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBaUx4dFpNV2M3NTJ2WjB1eC1rNnpvM3VIV0EyZFE_ZT12RExKQWY/root/content"><img src="download_icon.png" alt="Download for Windows"></a></td>
    <td style="text-align: center;"><a href="https://api.onedrive.com/v1.0/shares/u!aHR0cHM6Ly8xZHJ2Lm1zL3UvcyFBaUx4dFpNV2M3NTJ2WjB0T2trMTczXzl4ak4zN2c_ZT1nY1hmaXI/root/content"><img src="download_icon.png" alt="Download for Debian/Ubuntu"></a></td>
    </tr>
    <tr>
    <td>
      <strong>SHA256 Checksum:</strong> 31B8A09E8198CE01B44B391C38C23E3B789D107E1998A70C1AF61422304F8C2C
    </td>
    <td>
      <strong>SHA256 Checksum:</strong> 8CC6FB183A70300C8D37EBD6D5ECCD26ADE71ECEFB86AAE0515EE7731F25F733
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
