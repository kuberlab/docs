

To use the Dataset object in the **Kibernetika** project, a user needs to add ***Dataset*** as a source in the project, and it will become available to the Jupyter Notebook as well as the Python or R execution environments.

To configure this, select the storage type ‘dataset’, and choose the required dataset and version from the list displayed (see figure below).

![](../img/datasets/img1.png)

Now you can see the data set as a folder in Jupyter Notebook. In workflow tasks it will be accessible by the use of environment variables.

![](../img/datasets/img2.png)

Both the Jupyter Notebook, and the Python and R environments can access the data files stored in the data set directories chosen.

![](../img/datasets/img3.png)

Because data sets can be very big, the loading of the data needs to be done from the command line and not the browser interface. **Kibernetika** has provided the ***kdataset*** utility to facilitate operations with data sets.

Before loading the first version of the data set, the Dataset object needs to be created. That can be done in the GUI in the ***Dataset*** section of your workspace. Or, the data set can be created during the downloading of the data by using “--create” or “--force” flags in the ‘push’ command.


