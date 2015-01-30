# ubuntu-tk-12.04

Assuming a working docker setup, build with `make`.

This takes the vanilla ubuntu:12.04 image and preinstalls busser,
busser-serverspec & serverspec. This typically cuts almost 5 minutes of
wall time off of my test-kitchen runs.

## Configuring test-kitchen

By default, Test-Kitchen installs busser and friends into `/tmp/busser`
but this Dockerfile installs it into `/opt/busser` so that it will
persist across container destruction/creation. To tell Test-Kitchen
about this, your `.kitchen.yml` file should contain something like the
following:

```
platforms:
  - name: ubuntu-12.04
    driver_config:
      image: ubuntu-tk:12.04
      platform: ubuntu
      root_path: /opt/busser
```
