---
title: Connect to Your TiDB Cluster
summary: Connect to your TiDB cluster via a SQL client or SQL shell.
---

# Connect to Your TiDB Cluster

After your TiDB cluster is created on TiDB Cloud, you can use one of the following three methods to connect to your TiDB cluster. You can access your cluster via a SQL client, or quickly via SQL Shell in the TiDB Cloud Console.

+ Connect via a SQL client

    - [Connect via standard connection](#connect-via-standard-connection): The standard connection exposes a public endpoint with traffic filters, so you can connect to your TiDB cluster from your laptop.
    - [Connect via VPC peering](#connect-via-vpc-peering): If you want lower latency and more security, set up VPC peering and connect via a private endpoint using a VM instance on the corresponding cloud provider in your cloud account.

- [Connect via SQL shell](#connect-via-sql-shell): to try TiDB SQL and test out TiDB's compatibility with MySQL quickly, or administer user privileges

## Connect via standard connection

To connect to your TiDB cluster via standard connection, perform the following steps:

1. Navigate to the **TiDB Cluster** page and find your newly created cluster.

2. Click **Connect**. The **Connect to TiDB** dialog displays.

3. Create the traffic filter for the cluster. Traffic filter is a list of IPs and CIDR addresses that are allowed to access TiDB Cloud via SQL client.

    If it is the first time that you connect to the cluster, the traffic filter is empty by default. Perform the following sub-steps to add one. If the traffic filter is already set, skip this step.

    1. Click one of the buttons to add some rules quickly.

        - **Add Your Current IP Address**
        - **Add Rules from Default Set**
        - **Allow Access from Anywhere**

    2. Provide an optional description for the newly added IP address or CIDR range.

    3. Click **Create Filter** to confirm the changes.

4. Use a SQL client to connect to TiDB.

    {{< copyable "shell" >}}

    ```shell
    mysql -u root -h <endpoint> -P 4000 -p
    ```

    > **Note:**
    >
    > Currently, TiDB does not work well with MySQL client 8.0, so you need to use MySQL client 5.7. Or you can add the `--default-auth=mysql_native_password --default-character-set=utf8` command line option if you are using MySQL client 8.0.

## Connect via VPC peering

To connect to your TiDB cluster via VPC peering, perform the following steps:

1. Navigate to the **TiDB Cluster** page and find your newly created cluster.

2. Click **Connect**, and select the **VPC Peering** tab at the **Connect to TiDB** dialog.

3. Set up VPC peering. See [Set up VPC Peering](set-up-vpc-peering-connections.md) for details.

4. Click **Get Endpoint** and wait for a few minutes. Then the connection command displays in the dialog.

5. Use a SQL client to connect to TiDB from your server which has set up VPC peering with TiDB Cloud.

    {{< copyable "shell" >}}

    ```shell
    mysql -u root -h <endpoint> -P 4000 -p
    ```

    > **Note:**
    >
    > Currently, TiDB does not work well with MySQL client 8.0, so you need to use MySQL client 5.7. Or you can add the `--default-auth=mysql_native_password --default-character-set=utf8` command line option if you are using MySQL client 8.0.

## Connect via SQL Shell

To connect to your TiDB cluster using SQL shell, perform the following steps:

1. Navigate to the **TiDB Cluster** page and find your newly created cluster.

2. Click **Connect**, and select the **Web SQL Shell** tab at the **Connect to TiDB** dialog.

3. Click **Open SQL Shell**.

4. On the prompted **TiDB password** line, enter the root password of the current cluster. Then your application is connected to the TiDB cluster.

## What's next

After you have successfully connected to your TiDB cluster, you can [explore SQL statements with TiDB](https://pingcap.com/docs/stable/basic-sql-operations/).
