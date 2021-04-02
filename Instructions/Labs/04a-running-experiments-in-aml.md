---
lab:
    title: 'Running experiments in Azure Machine Learning'
---
# Running experiments in Azure Machine Learning

Machine Learning is primarily about training models that you can use to provide predictive services to applications. In this exercise, you will learn to run experiments in Azure Machine Learning from Azure Databricks.

## Unit Pre-requisites

**Complete Lab 01a**: Before you can run this lab, you will need to complete [Lab 01a](https://github.com/MicrosoftLearning/dp-090-databricks-ml/blob/master/Instructions/Labs/01a-introduction-to-azure-databricks.md), Getting Started with Azure Databricks.  This includes important steps such as creating a cluster, uploading notebooks, and uploading the NYC Taxi & Limousine Commission - green taxi trip records dataset.

## Install libraries on the Azure Databricks Cluster

The notebooks you will run depends on certain Python libraries that will need to be installed in your cluster. The following steps walk you through adding these dependencies.

- From within the Azure Databricks workspace, from the `Clusters` section, select your cluster. Make sure the state of the cluster is `Running`.
- Select the **Libraries** link and then select **Install New**.
- In the Library Source, select **PyPi** and in the `Package` text box type `azureml-sdk[databricks]` and select **Install**.
- Next install `sklearn-pandas==2.1.0`
- Next install `azureml-mlflow`

    ![Install library dialog](images/04-azure-databricks-install-library.png 'Install Library Dialog')

## Deploy an Azure Machine Learning workspace

1. If you have already created an Azure Machine Learning workspace in your subscription, you can skip to the section [Exercise: Running experiments in Azure Machine Learning](#Exercise-Running-experiments-in-Azure-Machine-Learning).

1. In the [Azure Portal](https://portal.azure.com/#home), select **+ Create a resource**, then type `Machine Learning` into the search bar.

1. Select the product **Machine Learning** and then select **Create**.

    ![Create Azure Machine Learning workspace](images/04-create-aml-ws-01.png 'Create AML workspace')

1. In the Create Machine Learning Workspace dialog that appears, provide the following values:

   - **Subscription**: Choose your Azure subscription.
   - **Resource group**: Select the resource group in which you deployed your Azure Databricks workspace.
   - **Workspace Name**: `aml-ws`
   - **Region**: Choose a region closest to you (it is OK if the Azure Databricks Workspace and the Azure Machine Learning Workspace are in different locations).

1. Select **Review + Create** and then select **Create** when the form values passes validation.

    ![Create Azure Machine Learning workspace](images/04-create-aml-ws-02.png 'Create AML workspace')

## Exercise: Running experiments in Azure Machine Learning

In this exercise, you will learn to run experiments in Azure Machine Learning from Azure Databricks.

1. Within the Azure Databricks Workspace, using the command bar on the left, select **Workspace**, **Users** and select your username (the entry with house icon). Open the folder named **04 - Integrating Azure Databricks and Azure Machine Learning** to find the notebook **1.0 Running experiments in Azure Machine Learning**.

1. Then read the notes in the notebook, running each code cell in turn. After completing the exercises in the notebook continue below to review the training metrics and artifacts for your experiment.

1. From within the Azure Machine Learning studio, navigate to the **Experiments** tab, and open the experiment run that corresponds to the MLflow experiment. In the **Metrics** tab of the run, you will observe the model metrics that were logged via MLflow tracking APIs.

    ![Model metrics](images/04-01-03-01-AML-metrics.png 'Model Metrics')

1. Next, when you open the **Outputs + logs** tab you will observe the model artifacts that were logged via MLflow tracking APIs.

    ![Model artifacts](images/04-01-03-01-AML-artifacts.png 'Model Artifacts')

## Clean-up

If you're finished working with Azure Databricks for now, in Azure Databricks workspace, on the **Clusters** page, select your cluster and select **Terminate** to shut it down. Otherwise, leave it running for the next exercise.
