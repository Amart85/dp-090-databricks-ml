---
lab:
    title: 'Train a model with AutoML'
---

# Train a model with AutoML

AutoML is a feature of Azure Databricks that tries multiple algorithms and parameters with your data to train an optimal machine learning model.

This exercise should take approximately **45** minutes to complete.

## Before you start

You'll need an [Azure subscription](https://azure.microsoft.com/free) in which you have administrative-level access.

## Provision an Azure Databricks workspace

An Azure Databricks workspace provides a central cloud-based environment for all your data science activities in Azure Databricks. You can create a workspace interactively in the Azure portal or use one you already have, but we recommend you follow the steps below to use a script to provision a suitable workspace for this exercise.

> **Note**: For this exercise, you need a **Premium** Azure Databricks workspace in a region where *model serving* is supported. See [Azure Databricks regions](https://learn.microsoft.com/azure/databricks/resources/supported-regions) for details of regional Azure Databricks capabilities. A Premium workspace is not required to use AutoML to train a model, but it *is* required to deploy a model.

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
    cd dp-090/Allfiles/labs/03
    ./setup.ps1
    ```

6. If prompted, choose which subscription you want to use (this will only happen if you have access to multiple Azure subscriptions).

7. Wait for the script to complete - this typically takes around 5 minutes, but in some cases may take longer. While you are waiting, review the [What is AutoML?](https://learn.microsoft.com/azure/databricks/machine-learning/automl/) article in the Azure Databricks documentation.

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
    - **Cluster Mode**: Single Node
    - **Access mode**: Single user
    - **Single user access**: *Your user ID*
    - **Databricks Runtime Version**: *Select the **<u>ML</u>** edition of the latest available version of the runtime (**Not** a Standard runtime version) that:*
        - *Does **not** use a GPU*
        - *Includes Scala > **2.11***
        - *Includes Spark > **3.0***
    - **Node Type**: Standard_DS3_v2
    - **Terminate after**: 30 minutes of inactivity

7. Wait for the cluster to be created and started. It may take a minute or two.

> **Note**: If your cluster fails to start, your subscription may have insufficient quota in the region where your Azure Databricks workspace is provisioned. See [CPU core limit prevents cluster creation](https://docs.microsoft.com/azure/databricks/kb/clusters/azure-core-limit) for details. If this happens, you can try deleting your workspace and creating a new one in a different region. You can specify a region as a parameter for the setup script like this: `./setup.ps1 eastus`

## Upload data to a table in Azure Databricks

To train a machine learning model, you need a source of training data. In this exercise, you'll train a model to classify a penguin as one of three species based on observations including its location and body measurements. You'll load training data that includes the species label into a table in your Azure Databricks workspace.

1. Download the following data file to your local computer, saving it as **penguins.csv** in any folder.

   - [https://raw.githubusercontent.com/MicrosoftLearning/dp-090-databricks-ml/master/data/penguins.csv](https://raw.githubusercontent.com/MicrosoftLearning/dp-090-databricks-ml/master/data/penguins.csv)

1. In the Azure Databricks Workspace, at the top of the sidebar on the left, switch the persona to **Machine Learning**. Then select **Data**.
1. In the **data**page, in the **+ Add** menu, select **Add data**. Then select the option to **Upload data** and upload the **penguins.csv** file you saved previously.
1. Review the uploaded data, and then use the **Create table** button to create a new table named **penguins** based on the data in the file.

## Create an AutoML experiment

Now that you have some data, you can use it with AutoML to train a model.

1. In the sidebar on the left, select **Experiments**.
1. On the **Experiments** page, select **Create an AutoML experiment**.
1. Configure the AutoML experiment wuth the following settings:
    - **Cluster**: *Select your cluster*
    - **ML problem type**: Classification
    - **Input training dataset**: *In the **default** database, select the **penguins** table*
    - **Prediction target**: Species
    - **Experiment name**: Penguin-classification
    - **Advanced configuration**:
        - **Evaluation metric**: Precision
        - **Training frameworks**: lighgbm, scikit-learn, xgboost
        - **Timeout**: 5
        - **Time column for training/validation/testing split**: *Leave blank*
        - **Positive label**: *Leave blank*
        - **Intermediate data storage location**: MLflow Artifact
1. Use the **Start AutoML** button to start the experiment. Close any information dialogs that are displayed.
1. Wait for the experiment to complete. You can use the **Refresh** button on the right to view details of the runs that are generated.
1. After five minutes, the experiment will end. Refreshing the runs will show the run that resulted in the best performing model (based on the *precision* metric you selected) at the top of the list.

## Deploy the best performing model

Having run an AutoML experiment, you can explore the best performing model that it generated.

1. In the **Penguin-classification** experiment page, select **View notebook for best model** to open the notebook used to rain the model in a new browser tab.
1. Scroll through the cells in the notebook, noting the code that was used to train the model.
1. Close the browser tab containing the notebook to return to the **Penguin-classification** experiment page.
1. In the list of runs, select the name of the first run (which produced the best model) to open it.
1. In the **Artifacts** section, note that the model has been saved as an MLflow artifact. Then use the **Register model** button to register the model as a new model named **Penguin-Classifier**.
1. In the sidebar on the left, switch to the **Models** page. Then select the **Penguin-Classifier** model you just registered.

    > **Note**: The remainder of this exercise requires a *Premium* Azure Databricks workspace.

1. On the **Penguin-Classifier** page, use the **Use model for inferencing** button to create a new real-time endpoint with the following settings:
    - **Model**: Penguin Classifier
    - **Model version**: 1
    - **Endpoint**: classify-penguin
    - **Compute size**: Small

    The serving endpoint is hosted in a new cluster, which it may take several minutes to create.
  
1. When the endpoint has been created, use the **Query endpoint** button at the top right to open an interface from which you can test the endpoint. Then in the test interface, on the **Browser** tab, enter the following JSON request and use the **Send Request** button to call the endpoint and generate a prediction.

    ```json
    {
      "dataframe_records": [
      {
         "Island": "Biscoe",
         "CulmenLength": 48.7,
         "CulmenDepth": 14.1,
         "FlipperLength": 210,
         "BodyMass": 4450
      }
      ]
    }
    ```

1. Experiment with a few different values for the penguin features and observe the results that are returned. Then, close the test interface.

## Delete the endpoint

When the endpoint is not longer required, you should delete it to avoid unnecessary costs.

In the **classify-penguin** endpoint page, in the **&#8285;** menu, select **Delete**.

## Clean-up

If you're finished working with Azure Databricks for now, in Azure Databricks workspace, on the **Compute** page, select your cluster and select **&#9632; Terminate** to shut it down.

You can then close the Azure Databricks web portal, return to the Azure portal, and delete the **dp090-*xxxxxxx*** resource group containing your Azure Databricks workspace.
