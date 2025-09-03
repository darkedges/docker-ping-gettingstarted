# Purpose

This directory contains the data that is required to customize PingFederate containers to taste
The file system structure must follow that of a pingfederate instance.
These files are laid over a vanilla installation of pingfederate

## Credentials

User: Administrator
Password: 2FederateM0re ( that's a zero numeral, not uppercase O )

## Export Config

```console
curl --location --request GET 'https://localhost:9999/pf-admin-api/v1/bulk/export' --header 'X-XSRF-Header: PingFederate' --user "administrator:Passw0rd" -k > bulk-export/shared/data.json
docker run --rm -v $PWD/bulk-export/shared:/shared darkedges/ping-bulkexport-tools:latest /shared/pf-config.json /shared/data.json /shared/env_vars /shared/data.json.subst > bulk-export/shared/convert.log
cp bulk-export/shared/data.json.subst console/instance/bulk-config/
```
