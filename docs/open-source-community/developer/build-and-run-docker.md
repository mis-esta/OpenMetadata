# Build and Run Docker

## Run Docker (Local Server)

{% hint style="info" %}
This Docker will enable users to access the Local OpenMetadata Server and Ingestion.

**Prerequisites**

* Docker >= 20.10.x
* Minimum allocated memory to Docker >= 4GB (Preferences -> Advanced -> Resources)
{% endhint %}

Run the below script to create the latest Maven build of the local and run the Docker with the respective Maven build and Ingestion.

```
#Run Script to initialize Maven Build and start building Docker
git clone https://github.com/open-metadata/OpenMetadata
cd OpenMetadata
./docker/run_local_docker.sh
```
