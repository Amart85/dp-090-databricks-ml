---
lab:
    title: 'Using MLflow to Track Experiments'
    module: 'Module 3 - Managing Experiments and Models'
---

# Using MLflow to Track Experiments

MLflow is a fully-featured model tracking and registry system.  In this exercise, you will use MLflow to collect model training artifacts, metrics, and parameters.  You will then be able to view those outputs through the Azure Databricks UI or programmatically. To begin, you need to have access to an Azure Databricks workspace with an interactive cluster. If you do not have a workspace and/or the required cluster, follow the instructions below. Otherwise, you can skip to the section [Upload the Databricks notebook archive](#Upload-the-Databricks-notebook-archive).

## Prerequisites

**Complete Lab 01a**: Before you can run this lab, you will need to complete [Lab 01a](https://github.com/MicrosoftLearning/dp-090-databricks-ml/blob/master/Instructions/Labs/01a-introduction-to-azure-databricks.md), Getting Started with Azure Databricks.  This includes important steps such as creating a cluster, uploading notebooks, and uploading the NYC Taxi & Limousine Commission - green taxi trip records dataset.

## Use MLflow to Track Experiments

In this exercise, you will learn to prepare training data for machine learning purposes as shown in the notebook.

1. Within the Azure Databricks Workspace, using the command bar on the left, select **Workspace**, **Users** and select your username (the entry with house icon). Open the folder named **03 - Managing Experiments and Models** to find the notebook **01 - Using MLflow to Track Experiments**.

1. If your cluster is not running, go to `Clusters`, select your cluster and press the `Start` button, then press `Confirm`. Wait until the cluster is started.

1. Attach the notebook to your cluster. Go to the top left dropdown menu and choose your cluster to attach your notebook to that cluster. Alternately, you can do this later, when running the first cell in a detached notebook: a confirmation dialog appears, warning that the notebook is not yet attached to any cluster, asking if you want to automatically launch a cluster, press `Attach and Run` to do so.

1. Then read the notes in the notebook, running each code cell in turn.  In the section entitled **View the Experiment, Runs, and Run Details with the Databricks UI**, there will be instructions on what actions to perform, as these actions will take place outside of the confines of a notebook.  It may be easiest to open up a second tab in your browser and perform these actions in that tab while reviewing the instructions in the notebook.

## Clean-up

If you're finished working with Azure Databricks for now, in Azure Databricks workspace, on the **Clusters** page, select your cluster and select **Terminate** to shut it down. Otherwise, leave it running for the next exercise.
