---
lab:
    title: 'Working with Data in Azure Databricks'
    module: 'Module 1 - Introduction to Azure Databricks'
---

# Working with Data in Azure Databricks

You will learn to load data by using DBFS and manipulate it by using Spark Dataframes.
Databricks File System (DBFS) is a distributed file system mounted into a Databricks workspace and available on Databricks clusters.
DataFrames are the distributed collections of data allowing the processing of huge amounts of data.

## Prerequisites

Assuming you have completed the previous lab, you have a working setup already. A cluster is available and your workspace exists.

Also, the notebook and the required data has been already imported.

## Work with Data in Azure Databricks

In this exercise, you will learn how to load and manipulate data inside the Azure Databricks environment.

1. Within the Azure Databricks Workspace, using the command bar on the left, select **Workspace**, **Users** and select your username (the entry with house icon). Open the folder named **01 - Introduction to Azure Databricks** to find the notebook **Working with data in Azure Databricks**.

1. If your cluster is not running, go to `Clusters`, select your cluster and press the `Start` button, then press `Confirm`. Wait until the cluster is started.

1. Attach the notebook to your cluster. Go to the top left dropdown menu and choose your cluster to attach your notebook to that cluster. Alternately, you can do this later, when running the first cell in a detached notebook: a confirmation dialog appears, warning that the notebook is not yet attached to any cluster, asking if you want to automatically launch a cluster, press `Attach and Run` to do so.

1. Read the notes in the notebook, running each code cell in turn.

## Clean-up

If you're finished working with Azure Databricks for now, in Azure Databricks workspace, on the **Clusters** page, select your cluster and select **Terminate** to shut it down. Otherwise, leave it running for the next exercise.
