# dell-omreport-parser

## What is it?

This tool uses the Dell `omreport` tool to output an XML, format it to a JSON, and send it to an API server to gather inventory and trigger alerts.

Check the API section for info on the API/Web server.

## Compatability 

This has been tested with and written for OMSA Version 8.3.0

The temperature and power supply scripts have issues collecting data for OMSA Version 9.2.0. Workaround incoming

To find the version of OMSA running on your server (for Linux hosts at least), run `/opt/dell/srvadmin/sbin/omreport about`
## How To

- Clone repo in `/opt/`

- Move `omsa-scripts/config.example.py` to `omsa-scripts/config.py`

- Edit `omsa-scripts/config.py`
    - `host` is the name of the server
    - `api_server` is the OMSA-Web server. See the API section for more info.
    - `verify_ssl` determines whether or not `requests` will verify the TLS certificate when posting metrics

- Run `install.sh` as root

If you want to clone the repo elsewhere, you'll need to modify `/etc/cron.d/omsa-metrics`.

## API

Metrics are sent to an API server that you define. 

The API server can be found in [this repo](https://github.com/mitchya1/dell-omreport-web)
