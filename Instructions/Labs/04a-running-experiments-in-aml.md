---
lab:
    title: 'Running experiments in Azure Machine Learning'
    module: 'Module 4 - Integrating Azure Databricks and Azure Machine Learning'
---

# Running experiments in Azure Machine Learning

Machine Learning is primarily about training models that you can use to provide predictive services to applications. In this exercise, you will learn to run experiments in Azure Machine Learning from Azure Databricks.

## Prerequisites

Before starting this lab, complete the **Getting Started with Azure Databricks** lab to set up your Azure Databricks environment and import the data and notebooks you require.

## Install libraries on the Azure Databricks Cluster

The notebooks you will run depends on certain Python libraries that will need to be installed in your cluster. The following steps walk you through adding these dependencies.

- From within the Azure Databricks workspace, from the **Clusters** section, select your cluster. Make sure the state of the cluster is **Running**.
- Select the **Libraries** link and then select **Install New**.
- In the Library Source, select **PyPi** and in the **Package** text box type `azureml-sdk[databricks]` and select **Install**.
- Next install `sklearn-pandas==2.1.0`
- Next install `azureml-mlflow`

## Deploy an Azure Machine Learning workspace

1. If you have already created an Azure Machine Learning workspace in your subscription, you can skip to the section [Exercise: Running experiments in Azure Machine Learning](#Exercise-Running-experiments-in-Azure-Machine-Learning).

1. In the [Azure Portal](https://portal.azure.com/#home), create a new resource: **Machine Learning**

1. In the Create Machine Learning Workspace dialog that appears, provide the following values:

   - **Subscription**: Choose your Azure subscription.
   - **Resource group**: Select the resource group in which you deployed your Azure Databricks workspace.
   - **Workspace Name**: aml-ws
   - **Region**: Choose a region closest to you (it is OK if the Azure Databricks Workspace and the Azure Machine Learning Workspace are in different locations).

1. Review and complete the creation of Azure Machine Learning workspace.

## Run an experiment in Azure Machine Learning

In this exercise, you will learn how to load and manipulate data inside the Azure Databricks environment.

1. In a web browser, open your Azure Databricks workspace.

1. If your cluster is not running, on the **Compute** page, select your cluster and use the **&#9654; Start** button to start it

1. In the Azure Databricks Workspace, using the command bar on the left, select **Workspace**. Then select **Users**, and **&#9751; *your_user_name***. Then in the folder named **04 - Integrating Azure Databricks and Azure Machine Learning**, open the **1.0 Running experiments in Azure Machine Learning** notebook.

1. Attach the notebook to your cluster. Then read the notes in the notebook, running each code cell in turn.

## Clean-up

If you're finished working with Azure Databricks for now, in Azure Databricks workspace, on the **Compute** page, select your cluster and select **&#9632; Terminate** to shut it down. Otherwise, leave it running for the next exercise.
