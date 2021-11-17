---
description: This guide will help install DBT connector and run manually
---

# DBT

{% hint style="info" %}
**Prerequisites**

OpenMetadata is built using Java, DropWizard, Jetty, and MySQL.

1. Python 3.7 or above
{% endhint %}

### Install from PyPI

{% tabs %}
{% tab title="Install Using PyPI" %}
```bash
pip install 'openmetadata-ingestion[dbt]'
```
{% endtab %}
{% endtabs %}

### Run Manually

```bash
metadata ingest -c ./examples/workflows/dbt.json
```

### Configuration

{% code title="dbt.json" %}
```javascript
{
  "source": {
    "type": "dbt",
    "config": {
      "service_name": "bigquery",
      "service_type": "BigQuery",
      "catalog_file": "./examples/sample_data/dbt/catalog.json",
      "manifest_file": "./examples/sample_data/dbt/manifest.json",
      "run_results_file": "./examples/sample_data/dbt/run_results.json",
      "database": "shopify"
    }
  },
 ...
```
{% endcode %}

1. **service\_name** - Service Name for this DBT cluster.
2. **catalog\_file **- path to the catalog file
3. **manifest\_file **-** **path to the manifest file
4. **run\_results\_file **- path to the run results file** **

## Publish to OpenMetadata

Below is the configuration to publish DBT data into the OpenMetadata service.

Add optionally `pii` processor and `metadata-rest` sink along with `metadata-server` config

{% code title="dbt.json" %}
```javascript
{
  "source": {
    "type": "dbt",
    "config": {
      "service_name": "bigquery",
      "service_type": "BigQuery",
      "catalog_file": "./examples/sample_data/dbt/catalog.json",
      "manifest_file": "./examples/sample_data/dbt/manifest.json",
      "run_results_file": "./examples/sample_data/dbt/run_results.json",
      "database": "shopify"
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
