# mender-docker-action

The mender-docker-action is a very lightweight Github action which allows you to upload Mender Update Module artifacts using `mender-artifact` 3.7.1 and Python 3.9 via Mender basic auth and Mender's RESTful API.

## Example usage

```yaml
on: [push]

jobs:
  push-mender-artifact:
    runs-on: ubuntu-latest
    name: Mender artifact pipeline
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: Upload Mender artifact
        uses: Cein-Markey/mender-docker-action@v0.2.0-alpha
        id: mender-artifact-upload
        with:
          mender-device-type: raspberrypi3
          mender-device-release: release-v0.1.0
          mender-device-update-module: dockerservice
          mender-device-update-module-files: "foo.txt,bar.txt" #root files from actions/checkout@v3
          mender-device-group: staging
          mender-auth-username: username
          mender-auth-password: password
```