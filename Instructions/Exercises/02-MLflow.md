---
lab:
    title: 'Use MLflow in Azure Databricks'
---

# Use MLflow in Azure Databricks

In this exercise, you'll explore techniques for preparing data and training machine learning models in Azure Databricks.

This exercise should take approximately **45** minutes to complete.

## Before you start

You'll need an [Azure subscription](https://azure.microsoft.com/free) in which you have administrative-level access.

## Provision an Azure Databricks workspace

An Azure Databricks workspace provides a central cloud-based environment for all your data science activities in Azure Databricks.

> **Note**: For this exercise, you need a **Premium** Azure Databricks workspace in a region where *model serving* is supported. See [Azure Databricks regions](https://learn.microsoft.com/azure/databricks/resources/supported-regions) for details of regional Azure Databricks capabilities.

You can create a workspace interactively in the Azure portal or use one you already have, but we recommend you follow the steps below to use a script to provision a suitable workspace for this exercise.

1. In a web browser, sign into the [Azure portal](https://portal.azure.com) at `https://portal.azure.com`.
2. Use the **[\>_]** button to the right of the search bar at the top of the page to create a new Cloud Shell in the Azure portal, selecting a ***PowerShell*** environment and creating storage if prompted. The cloud shell provides a command line interface in a pane at the bottom of the Azure portal, as shown here:

    ![Azure portal with a cloud shell pane](./images/cloud-shell.png)

    > **Note**: If you have previously created a cloud shell that uses a *Bash* environment, use the the drop-down menu at the top left of the cloud shell pane to change it to ***PowerShell***.

3. Note that you can resize the cloud shell by dragging the separator bar at the top of the pane, or by using the **&#8212;**, **&#9723;**, and **X** icons at the top right of the pane to minimize, maximize, and close the pane. For more information about using the Azure Cloud Shell, see the [Azure Cloud Shell documentation](https://docs.microsoft.com/azure/cloud-shell/overview).

4. In the PowerShell pane, enter the following commands to clone this repo:

    ```
    rm -r dp-090 -f
    git clone https://github.com/MicrosoftLearning/dp-090-databricks-ml dp-090
    ```

5. After the repo has been cloned, enter the following commands to change to the folder for this lab and run the **setup.ps1** script it contains:

    ```
    cd dp-090/Allfiles/labs/02
    ./setup.ps1
    ```

6. If prompted, choose which subscription you want to use (this will only happen if you have access to multiple Azure subscriptions).

7. Wait for the script to complete - this typically takes around 5 minutes, but in some cases may take longer. While you are waiting, review the [Concepts](https://mlflow.org/docs/latest/concepts.html) article in the MLflow documentation.

## Create a cluster

Azure Databricks is a distributed processing platform that uses Apache Spark *clusters* to process data in parallel on multiple nodes. Each cluster consists of a driver node to coordinate the work, and worker nodes to perform processing tasks.

> **Note**: In this exercise, you'll create a *single-node* cluster to minimize the compute resources used in the lab environment (in which resources may be constrained). In a production environment, you'd typically create a cluster with multiple worker nodes.

1. In the Azure portal, browse to the **dp090-*xxxxxxx*** resource group that was created by the script you ran.
2. Select your Azure Databricks Service resource (which will have a name similar to **databricks*xxxxxxx***).
3. In the **Overview** page for your workspace, use the **Launch Workspace** button to open your Azure Databricks workspace in a new browser tab; signing in if prompted.
4. If a **What's your current data project?** message is displayed, select **Finish** to close it. Then view the Azure Databricks workspace portal and note that the sidebar on the left side contains icons for the various tasks you can perform. The sidebar expands to show the names of the task categories.
5. Select the **(+) New** task, and then select **Cluster**.

    **Note**: If a tip is displayed, use the **Got it** button to close it. This applies to any future tips that may be displayed as you navigate the workspace interface for the first time.

6. In the **New Cluster** page, create a new cluster with the following settings:
    - **Name**: *Your name's* cluster (*default*)
    - **Policy**: Unrestricted
    - **Cluster Mode**: Single Node
    - **Access mode**: Single user
    - **Single user access**: *Your user ID*
    - **Databricks Runtime Version**: *Select the **<u>ML</u>** edition of the latest available version of the runtime (**Not** a Standard runtime version) that:*
        - *Does **not** use a GPU*
        - *Includes Scala > **2.11***
        - *Includes Spark > **3.0***
    - **Node Type**: Standard_DS3_v2
   - **Terminate after**: 30 minutes of inactivity

7. Wait for the cluster to be created. It may take a minute or two.

> **Note**: If your cluster fails to start, your subscription may have insufficient quota in the region where your Azure Databricks workspace is provisioned. See [CPU core limit prevents cluster creation](https://docs.microsoft.com/azure/databricks/kb/clusters/azure-core-limit) for details. If this happens, you can try deleting your workspace and creating a new one in a different region. You can specify a region as a parameter for the setup script like this: `./setup.ps1 eastus`.

## Import and explore a notebook

The tasks and code used in this exercise are in a notebook that you will run in your cluster.

1. Download the following notebook file to your local computer, saving it as **MLflow.ipynb** in any folder.

   - [https://github.com/MicrosoftLearning/dp-090-databricks-ml/raw/master/notebooks/MLflow.ipynb](https://github.com/MicrosoftLearning/dp-090-databricks-ml/raw/master/notebooks/MLflow.ipynb)

1. In the Azure Databricks Workspace, at the top of the sidebar on the left, switch the persona to **Machine Learning**. Then select **Workspace**.
1. Select **Home** and then select the downwards pointing chevron (**v**) next to your name, and select **Import**.
1. On the **Import Notebooks** dialog, import the **MLflow.ipynb** notebook file you downloaded.
1. Select the imported **MLflow.ipynb** notebook to open it.
1. Select **Connect** and attach the notebook to the cluster you created earlier. *(Alternatively, you will be prompted to attach a cluster when running the first cell in an unattached notebook).*
1. Read the notes in the notebook, running each code cell in turn.

## Clean-up

If you're finished working with Azure Databricks for now, in Azure Databricks workspace, on the **Compute** page, select your cluster and select **&#9632; Terminate** to shut it down.

You can then close the Azure Databricks web portal, return to the Azure portal, and delete the **dp090-*xxxxxxx*** resource group containing your Azure Databricks workspace.
