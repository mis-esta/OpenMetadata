---
description: >-
  This is a quick start guide that will show you how to quickly start a
  standalone server.
---

# Run Manually

### Download the distribution

**Prerequisites**

{% hint style="info" %}
OpenMetadata is built using Java, DropWizard, Jetty, and MySQL.

1. Java 11 or above
2. MySQL 8 or above
{% endhint %}

{% tabs %}
{% tab title="Download the release" %}
Download the latest binary release from [OpenMetadata](https://github.com/open-metadata/OpenMetadata/releases/download/0.6.0/openmetadata-0.6.0.tar.gz), Once you have the tar file,

```bash
# untar it
tar -zxvf openmetadata-0.6.0.tar.gz

# navigate to directory containing the launcher scripts
cd openmetadata-0.6.0
```
{% endtab %}
{% endtabs %}

### Install on your local machine

#### macOS

1. Setup Database
   *   Install MySQL

       ```
        brew install mysql
       ```
   *   Configure MySQL

       ```
       mysqladmin -u root password 'yourpassword'
       mysql -u root -p
       ```
   *   Setup Database

       ```
       mysql -u root -p
       CREATE DATABASE openmetadata_db;
       CREATE USER 'openmetadata_user'@'localhost' IDENTIFIED BY 'openmetadata_password';
       GRANT ALL PRIVILEGES ON openmetadata_db.* TO 'openmetadata_user'@'localhost' WITH GRANT OPTION;
       commit;
       ```
2.  Run bootstrap scripts to initialize the database and tables

    ```
       cd openmetadata-0.6.0
       ./bootstrap/bootstrap_storage.sh migrate
    ```
3.  Start the OpenMetadata Server

    ```
       cd openmetadata-0.6.0 
       ./bin/openmetadata.sh start
    ```

### Ingest Sample Data

Previous steps start OpenMetadata server. To start using it we need to run ElasticSearch and Ingest Sample metadata. Please follow the below guide:

[Ingest Sample Data](../../install/metadata-ingestion/ingest-sample-data.md)
