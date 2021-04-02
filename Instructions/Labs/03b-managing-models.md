---
lab:
    title: 'Managing Models'
---
# Managing Models

The Azure Databricks model registry is a powerful tool for model registration, model versioning, and tagging models for deployment.  In this exercise, you will learn how to use the model registry, through both the User Interface as well as the MLflow API. To begin, you need to have access to an Azure Databricks workspace with an interactive cluster. If you do not have a workspace and/or the required cluster, follow the instructions below. Otherwise, you can skip to the section [Upload the Databricks notebook archive](#Upload-the-Databricks-notebook-archive).

## Unit Pre-requisites

**Complete Lab 01a**: Before you can run this lab, you will need to complete [Lab 01a](https://github.com/MicrosoftLearning/dp-090-databricks-ml/blob/master/Instructions/Labs/01a-introduction-to-azure-databricks.md), Getting Started with Azure Databricks.  This includes important steps such as creating a cluster, uploading notebooks, and uploading the NYC Taxi & Limousine Commission - green taxi trip records dataset.

## Exercise: Managing Models

In this exercise, you will learn to prepare training data for machine learning purposes as shown in the notebook.

1. Within the Azure Databricks Workspace, using the command bar on the left, select **Workspace**, **Users** and select your username (the entry with house icon). Open the folder named **03 - Managing Experiments and Models** to find the notebook **02 - Managing Models**.

1. Then read the notes in the notebook, running each code cell in turn.  For the first section, **Managing a Model via the User Interface**, there will be instructions on what actions to perform, as many of these actions will take place outside of the confines of a notebook.  It may be easiest to open up a second tab in your browser and perform these actions in that tab while reviewing the instructions in the notebook.

## Clean-up

If you're finished working with Azure Databricks for now, in Azure Databricks workspace, on the **Clusters** page, select your cluster and select **Terminate** to shut it down. Otherwise, leave it running for the next exercise.
