# Exercise 1: Getting Started with Azure ML

## Before You Start

Azure Machine Learning (Azure ML) is a Microsoft Azure-based service for running data science and machine learning workloads at scale in the cloud. To use Azure Machine Learning, you will need an Azure subscription.

## Task 1: Create an Azure ML Workspace

As its name suggests, a workspace is a centralized place to manage all of the Azure ML assets you need to work on a machine learning project.

1. Sign into the [Azure portal](https://portal.azure.com) and create a new **Machine Learning** resource, specifying a unique workspace name and creating a new resource group in a region of your choice. Select the **Enterprise** workspace edition.

   > **Note**:
   >
   >Basic edition workspaces have lower cost, but don't include capabilities like Auto ML, the Visual Designer, and graphical data drift monitoring. For more details, see [Azure Machine Learning pricing](https://azure.microsoft.com/en-us/pricing/details/machine-learning/).
   >
   > You can use any region in this lab, but if you plan to create GPU-based compute targets, you need to choose a region that supports the *NC-series* of VMs. Check the [Azure Products Available by Region page](https://azure.microsoft.com/en-us/global-infrastructure/services/?products=virtual-machines).

2. When the workspace and its associated resources have been created, view the workspace in the portal.

> **More Information**: To learn more about workspaces, see the [Azure ML Documentation](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-workspace).

## Task 2: Explore the Azure ML Studio Interface

You can manage workspace assets in the Azure portal, but for data scientists, this tool contains lots of irrelevant information and links that relate to managing general Azure resources. An alternative, Azure ML-specific web interface for managing workspaces is available.

> **Note**: The web-based interface for Azure ML is named *Studio*, which you may find confusing as there is also a free *Azure Machine Learning Studio* product for creating machine learning models using a visual designer. A more scalable version of this visual designer is included in the new Studio interface.

1. In the portal blade for your workspace, click the link to launch Studio; or alternatively, in a new browser tab, open [https://ml.azure.com](https://ml.azure.com). If prompted, sign in using the Microsoft account you used to sign into Azure in the previous task and select your Azure subscription and the workspace you created in the previous task.
2. View the Studio interface for your workspace - you can manage all of the assets in your workspace from here.

## Task 3: Create Compute Resources

You can run code to work with your workspace in many tools, including locally installed tools like Visual Studio Code or Jupyter Notebooks, or hosted environments like Azure Notebooks, or a JupyterHub server. Additionally, Azure ML includes the ability to create and manage Notebook VMs in your workspace, and that's what we'll use in this lab.

You'll also need cloud-based compute on which you can run experiments and training scripts at scale.

1. In the *Studio* web interface for your workspace, view the **Compute** page. This is where you'll manage all the compute targets for your data science activities.
2. On the **Notebook VMs** tab, add a new **Notebook VM**, giving it a unique name and using the default VM type template.
3. While the notebook VM is being created, switch to the **Training Clusters** tab, and add a new training cluster with the following settings:
    * **Compute name**: cpu-cluster
    * **Virtual Machine size**: Standard_DS12_v2
    * **Virtual Machine priority**: Dedicated
    * **Minimum number of nodes**: 0
    * **Maximum number of nodes**: 4
    * **Idle seconds before scale down**: 120

4. Note the **Inference Clusters** tab. This is where you can create and manage compute targets on which to deploy your trained models as web services for client applications to consume.

5. Note the **Attached Compute** tab. This is where you could attach cloud compute such as a virtual machine or Databricks cluster that exists outside of your workspace.

## Task 4: Get Started with the Azure ML SDK

You can perform most asset management tasks to set up your environment in the *Studio* interface, but it's also important to be able to script configuration tasks to make them easier to repeat and automate.

1. Return to the **Compute** page, view the **Notebook VMs** tab, and if necessary, wait until the Notebook VM has been created. Then verify that it is running, and then click the **Jupyter** link.
2. In the notebook environment, open a new **Terminal**, and in the **Users** folder, run the following command:

    ```bash
    git clone https://github.com/GraemeMalcolm/mlads-aml
    ```

3. After the comand has completed, close the terminal and view the home folder in your notebook file explorer - it should contain an **mlads-aml** folder, containing the files you will use in the rest of this lab.
4. In the **/mlads-aml/notebooks** folder, open the **01 - Getting Started.ipynb** notebook.
5. Read the notes in the notebook, running each code cell in turn.

> **Note**: If you intend to continue straight to the [next exercise](ex2.md), leave your Notebook VM running. If you're taking a break, you might want to close the Jupyter tabs and **Stop** your Notebook VM to avoid incurring unnecessary costs.
