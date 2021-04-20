---
lab:
    title: 'Preparing Data for Machine Learning'
    module: 'Module 2 - Training and Evaluating Machine Learning Models'
---

# Preparing Data for Machine Learning

Machine Learning is primarily about training models that you can use to provide predictive services to applications. In this exercise, you'll see how you can use Azure Databricks to prepare training data for machine learning purposes.

## Prerequisites

**Complete Lab 01a**: Before you can run this lab, you will need to complete [Lab 01a](https://github.com/MicrosoftLearning/dp-090-databricks-ml/blob/master/Instructions/Labs/01a-introduction-to-azure-databricks.md), Getting Started with Azure Databricks.  This includes important steps such as creating a cluster, uploading notebooks, and uploading the NYC Taxi & Limousine Commission - green taxi trip records dataset.

## Exercise: Preparing Data for Machine Learning

In this exercise, you will learn to prepare training data for machine learning purposes as shown in the notebook.

1. Within the Azure Databricks Workspace, using the command bar on the left, select **Workspace**, **Users** and select your username (the entry with house icon). Open the folder named **02 - Training and Evaluating Machine Learning Models** to find the notebook **1.0 Featurization**.

1. If your cluster is not running, go to `Clusters`, select your cluster and press the `Start` button, then press `Confirm`. Wait until the cluster is started.

1. Attach the notebook to your cluster. Go to the top left dropwdown and choose your cluster to attach your notebook to that cluster. Alternately, you can do this later, when running the first cell in a detached notebook: a confirmation dialog appears, warning that the notebook is not yet attached to any cluster, asking if you want to automatically launch a cluster, press `Attach and Run` to do so.

1. Then read the notes in the notebook, running each code cell in turn.

## Clean-up

If you're finished working with Azure Databricks for now, in Azure Databricks workspace, on the **Clusters** page, select your cluster and select **Terminate** to shut it down. Otherwise, leave it running for the next exercise.
