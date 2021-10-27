---
lab:
    title: 'Using MLflow to Track Experiments'
    module: 'Module 3 - Managing Experiments and Models'
---

# Using MLflow to Track Experiments

MLflow is a fully-featured model tracking and registry system.  In this exercise, you will use MLflow to collect model training artifacts, metrics, and parameters.  You will then be able to view those outputs through the Azure Databricks UI or programmatically. To begin, you need to have access to an Azure Databricks workspace with an interactive cluster. If you do not have a workspace and/or the required cluster, follow the instructions below. Otherwise, you can skip to the section [Upload the Databricks notebook archive](#Upload-the-Databricks-notebook-archive).

## Prerequisites

Before starting this lab, complete the [**Getting Started with Azure Databricks**](Instructions/Labs/01a-introduction-to-azure-databricks.md) lab to set up your Azure Databricks environment and import the data and notebooks you require. To use MLflow, you need to use a compute cluster with a **ML Databricks Runtime** version as instructed in the setup lab. This runtime will already include an installation of MLflow.

## Use MLflow to Track Experiments

In this exercise, you will learn how to load and manipulate data inside the Azure Databricks environment.

1. In a web browser, open your Azure Databricks workspace.

1. If your cluster is not running, on the **Compute** page, select your cluster and use the **&#9654; Start** button to start it

1. In the Azure Databricks Workspace, using the command bar on the left, select **Workspace**. Then select **Users**, and **&#9751; *your_user_name***. Then in the folder named **03 - Managing Experiments and Models**, open the **01 - Using MLflow to Track Experiments** notebook.

1. Attach the notebook to your cluster. Then read the notes in the notebook, running each code cell in turn.

> **Tip**: In the section entitled **View the Experiment, Runs, and Run Details with the Databricks UI**, there will be instructions on what actions to perform, as these actions will take place outside of the confines of a notebook.  It may be easiest to open up a second tab in your browser and perform these actions in that tab while reviewing the instructions in the notebook.

## Clean-up

If you're finished working with Azure Databricks for now, in Azure Databricks workspace, on the **Compute** page, select your cluster and select **&#9632; Terminate** to shut it down. Otherwise, leave it running for the next exercise.
