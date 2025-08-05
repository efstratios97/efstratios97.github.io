# Operations: Sophrosyne ©

The Open-Source version of Sophrosyne runs as standalone application but cannot be safely run in a distributed environment (Kubernetes). If you want to scale your Application, you can acquire the Enterprise Version.

## Configuration

Sophrosyne consists of 3 separate and decoupled services. They run with the following standard configuration.

* Sophrosyne-Database Service running on <strong>Port: 61997</strong>
* Sophrosyne-Server Service running on <strong>Port: 17609</strong>
* Sophrosyne-UI Service running on <strong>Port: 27697</strong>

### Configuration file

You can adjust the standard configuration via the configuration file `sophrosyne-operations.yml`. You can find under `C:\Program Files (x86)\Sophrosyne\config` or `/etc/sophrosyne/config`

```
sophrosyne:
  server:
    port: 17609
  db:
    host: localhost
    port: 61997
    user: postgres
    password: ""
    name: postgres
  telemetry:
    prometheus:
      standard_job:
        host: 0.0.0.0
        port: 27276
      high_loads_job:
        host: 0.0.0.0
        port: 27277
```