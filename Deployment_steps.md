# Deployment Steps

# Azure Data Ingestion Framework

Version: 1.0
Author: Mohammed Zubair Siddiqui

---

# 1. Introduction

This document describes the deployment process for the Azure Data Ingestion Framework.

The deployment includes:

* Resource provisioning
* Storage configuration
* Security setup
* Pipeline deployment
* Trigger configuration

---

# 2. Prerequisites

Ensure the following prerequisites are available:

* Active Azure Subscription
* Contributor access to Azure resources
* GitHub account
* Azure Data Factory access
* Azure SQL Database access

---

# 3. Create Resource Group

Create a dedicated Resource Group.

Example:

```text
rg-data-ingestion
```

Select the preferred Azure region.

---

# 4. Create Storage Account

Create an Azure Data Lake Storage Gen2 account.

Configuration:

* Hierarchical Namespace: Enabled
* Performance Tier: Standard
* Redundancy: GRS

Create the following containers:

```text
input/
output/
```

---

# 5. Create Folder Structure

Input folders:

```text
input/landing/
    csv/
    xml/
    json/
    sql/
```

Output folders:

```text
output/bronze/
    parquet/
```

---

# 6. Create Azure SQL Database

Deploy:

* SQL Server
* SQL Database

Configure:

* Firewall rules
* Azure services access

Verify database connectivity.

---

# 7. Create Azure Key Vault

Create Key Vault.

Store secrets for:

* SQL credentials
* Storage credentials
* Service credentials

Enable RBAC access control.

---

# 8. Create Azure Data Factory

Deploy Azure Data Factory.

Open ADF Studio.

---

# 9. Configure Linked Services

Create the following linked services:

* Azure Key Vault
* Azure SQL Database
* ADLS Gen2

Validate all connections.

---

# 10. Create Datasets

Create datasets for:

* CSV files
* XML files
* JSON files
* SQL tables
* Parquet output

Use parameterized datasets wherever possible.

---

# 11. Create Full Load Pipelines

Configure full load pipelines.

Features:

* Read complete datasets
* Convert to Parquet
* Store in output container

---

# 12. Create Incremental Load Pipelines

Configure incremental pipelines.

Methods:

* Timestamp filtering
* Last modified date
* Delta extraction

---

# 13. Configure Event Triggers

Create Blob Event Triggers.

Trigger conditions:

* Blob Created
* File uploaded

Supported file types:

* CSV
* XML
* JSON

---

# 14. Configure Schedule Triggers

Create schedule triggers.

Typical schedules:

* Daily
* Hourly
* Weekly

Used primarily for incremental loads.

---

# 15. Upload Sample Data

Upload files to the input container.

Example:

```text
input/landing/csv/
input/landing/xml/
input/landing/json/
```

---

# 16. Execute Pipelines

Run the pipelines manually or through triggers.

Verify:

* Successful execution
* File processing
* Data movement

---

# 17. Validate Output

Confirm that Parquet files are generated successfully.

Verify:

* Record counts
* Data integrity
* Folder structure

---

# 18. Monitoring

Monitor:

* Pipeline runs
* Activity logs
* Trigger executions

Investigate failures through ADF monitoring.

---

# 19. Troubleshooting

| Issue                  | Resolution                 |
| ---------------------- | -------------------------- |
| Pipeline failure       | Check linked services      |
| Authentication failure | Validate Key Vault secrets |
| Storage access issue   | Verify permissions         |
| Trigger failure        | Check event configuration  |
| SQL connectivity issue | Validate firewall settings |

---

# 20. Cleanup

After testing:

* Remove temporary files.
* Disable unused triggers.
* Delete unnecessary resources.

This helps reduce Azure costs.

---

# 21. Conclusion

Following these deployment steps enables the successful deployment of the Azure Data Ingestion Framework and allows secure, scalable, and reusable ingestion of multiple source systems into Azure Data Lake Storage Gen2.
