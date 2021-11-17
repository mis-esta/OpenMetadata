---
description: This guide will help install Glue connector and run manually
---

# Glue Catalog

{% hint style="info" %}
**Prerequisites**

OpenMetadata is built using Java, DropWizard, Jetty, and MySQL.

1. Python 3.7 or above
{% endhint %}

### Install from PyPI

{% tabs %}
{% tab title="Install Using PyPI" %}
```bash
pip install 'openmetadata-ingestion[glue]'
```
{% endtab %}
{% endtabs %}

### Run Manually

```bash
metadata ingest -c ./examples/workflows/glue.json
```

### Configuration

{% code title="glue.json" %}
```javascript
{
  "source": {
    "type": "glue",
    "config": {
      "aws_access_key_id": "aws_access_key_id",
      "aws_secret_access_key": "aws_secret_access_key",
      "database": "database",
      "region_name": "region_name",
      "endpoint_url": "endpoint_url",
      "service_name": "local_glue"
    }
  },
 ...
```
{% endcode %}

1. **aws\_access\_key\_id** - pass the AWS access key.
2. **aws\_secret\_access\_key** - pass the AWS secret access key.&#x20;
3. **database** - Database name from where data is to be fetched.
4. **region\_name** - Region name where the AWS instance is located.
5. **endpoint\_url** - The URL of the entry point for an AWS web service.
6. **service\_name** - Service Name for this Glue cluster.&#x20;
7. **filter\_pattern** - It contains includes, excludes options to choose which pattern of datasets.

## Publish to OpenMetadata

Below is the configuration to publish Glue data into the OpenMetadata service.

Add optionally `pii` processor and `metadata-rest` sink along with `metadata-server` config

{% code title="glue.json" %}
```javascript
{
  "source": {
    "type": "glue",
    "config": {
      "aws_access_key_id": "aws_access_key_id",
      "aws_secret_access_key": "aws_secret_access_key",
      "database": "database",
      "region_name": "region_name",
      "endpoint_url": "endpoint_url",
      "service_name": "local_glue"
    }
  },
  "sink": {
    "type": "metadata-rest",
    "config": {}
  },
  "metadata_server": {
    "type": "metadata-server",
    "config": {
      "api_endpoint": "http://localhost:8585/api",
      "auth_provider_type": "no-auth"
    }
  }
}
```
{% endcode %}

##
