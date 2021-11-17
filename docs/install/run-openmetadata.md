---
description: >-
  This installation doc will help you start a OpenMetadata standalone instance
  on your local machine.
---

# Run OpenMetadata

## Run Docker (Latest Release)

[Docker](https://docs.docker.com/get-started/overview/) is an open platform for developing, shipping, and running applications that enables you to separate your applications from your infrastructure so you can deliver software quickly using OS-level virtualization to deliver software in packages called containers.

{% hint style="info" %}
**Prerequisites**

* Docker >= 20.10.x
* Minimum allocated memory to Docker >= 4GB (Preferences -> Resources -> Advanced)
{% endhint %}

```bash
python3 -m pip install 'openmetadata-ingestion[docker]'
metadata docker --start
```

{% hint style="info" %}
**Note:**

* To stop the Docker containers: <mark style="color:orange;">`metadata docker --stop`</mark>
* To clean/prune the containers, volumes, and networks: <mark style="color:orange;">`metadata docker --clean`</mark>
{% endhint %}

### Next Steps

1. Docker for OpenMetadata will depend on Mysql Container to be up, It may take a few seconds to run.
2. Once OpenMetadata UI is accessible, Go to [Airflow UI](http://localhost:8080) to invoke the pipelines to ingest data.

The above command brings up all the necessary services

1. MySQL
2. ElasticSearch
3. OpenMetadata Sever
4. Ingestion with Airflow

To access the OpenMetadata

Open [http://localhost:8585](http://localhost:8585) in your browser

Airflow UI available at [http://localhost:8080](http://localhost:8080)

<mark style="color:purple;">(</mark><mark style="color:purple;">**username**</mark><mark style="color:purple;">: admin,</mark> <mark style="color:purple;">**password**</mark><mark style="color:purple;">: admin)</mark>

&#x20;
