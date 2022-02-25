---
lab:
    title: 'Managing Models'
    module: 'Module 3 - Managing Experiments and Models'
---

# Managing Models

The Azure Databricks model registry is a powerful tool for model registration, model versioning, and tagging models for deployment.  In this exercise, you will learn how to use the model registry, through both the User Interface as well as the MLflow API. To begin, you need to have access to an Azure Databricks workspace with an interactive cluster. If you do not have a workspace and/or the required cluster, follow the instructions below. Otherwise, you can skip to the section [Upload the Databricks notebook archive](#Upload-the-Databricks-notebook-archive).

## Prerequisites

Before starting this lab, complete the **Getting Started with Azure Databricks** lab to set up your Azure Databricks environment and import the data and notebooks you require.

## Manage Models

In this exercise, you will learn how to manage models.

1. In a web browser, open your Azure Databricks workspace.

1. If your cluster is not running, on the **Compute** page, select your cluster and use the **&#9654; Start** button to start it

1. In the Azure Databricks Workspace, using the command bar on the left, select **Workspace**. Then select **Users**, and **&#9751; *your_user_name***. Then in the folder named **03 - Managing Experiments and Models**, open the **02 - Managing Models** notebook.

1. Attach the notebook to your cluster. Then read the notes in the notebook, running each code cell in turn.

> **Tip**: For the first section, **Managing a Model via the User Interface**, there will be instructions on what actions to perform, as many of these actions will take place outside of the confines of a notebook.  It may be easiest to open up a second tab in your browser and perform these actions in that tab while reviewing the instructions in the notebook.

## Clean-up

If you're finished working with Azure Databricks for now, in Azure Databricks workspace, on the **Compute** page, select your cluster and select **&#9632; Terminate** to shut it down. Otherwise, leave it running for the next exercise.
