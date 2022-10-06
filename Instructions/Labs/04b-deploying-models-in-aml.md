---
lab:
    title: 'Deploying Models in Azure Machine Learning'
    module: 'Module 4 - Integrating Azure Databricks and Azure Machine Learning'
---

# Deploying Models in Azure Machine Learning

Machine Learning is primarily about training models that you can use to provide predictive services to applications. In this exercise, you will learn to train models in Azure Databricks and then deploy models in Azure Machine Learning.

## Prerequisites

Before starting this lab, complete the **Getting Started with Azure Databricks** and **Running experiments in Azure Machine Learning** lab to set up Azure Databricks and Azure machine Learning environments.

## Install libraries on the Azure Databricks Cluster

The notebooks you will run depends on certain Python libraries that will need to be installed in your cluster. The following steps walk you through adding these dependencies.

- From within the Azure Databricks workspace, from the **Clusters** section, select your cluster. Make sure the state of the cluster is **Running**.
- Select the **Libraries** link and then select **Install New**.
- In the Library Source, select **PyPi** and in the **Package** text box type `azureml-sdk[databricks]` and select **Install**.
- Next install `sklearn-pandas==2.1.0`
- Next install `azureml-mlflow`

## Deploy a Model in Azure Machine Learning

In this exercise, you will learn how to load and manipulate data inside the Azure Databricks environment.

1. In a web browser, open your Azure Databricks workspace.

1. If your cluster is not running, on the **Compute** page, select your cluster and use the **&#9654; Start** button to start it

1. In the Azure Databricks Workspace, using the command bar on the left, select **Workspace**. Then select **Users**, and **&#9751; *your_user_name***. Then in the folder named **04 - Integrating Azure Databricks and Azure Machine Learning**, open the **2.0 Deploying Models in Azure Machine Learning** notebook.

1. Attach the notebook to your cluster. Then read the notes in the notebook, running each code cell in turn.

## Clean-up

If you're finished working with Azure Databricks for now, in Azure Databricks workspace, on the **Compute** page, select your cluster and select **&#9632; Terminate** to shut it down.

If you have finished exploring Azure Databricks, you can delete the resource groups in your Azure subscription that contain the Azure Databricks and Azure Machine Learning resources.
