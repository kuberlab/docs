# Datasets

Recognizing the importance of the data, and complexity of the data processing, **Kibernetika** implemented the Dataset object. This object can be loaded, versioned, accessed, and commented on. The Dataset object can be published in the **Kibernetika** public catalog or it can be kept in a private workspace as well. **Kibernetika** also provides a number of open publicly available datasets as part of the public catalogs, so that using them is convenient and does not require further slow data downloads.

To use the Dataset object in the **Kibernetika** project, a user needs to add ***Dataset*** as a source in the project, and it will become available to the Jupyter Notebook as well as the Python or R execution environments.

# Create dataset

Dataset as a [usual catalog object](../catalog/catalog.md#datasets) can be created in UI. User should go to catalog in any organization, choose "Dataset" section in the left menu and click "(+) Add" button. Fill required field Name, Idenfification will be filled automatically if empty. Optional Description and Keywords also can be filled. "Published" checkbox should be checked if user wants his dataset will be available for all users.

![](../img/datasets-work-with/img1.png)

New dataset will be created after clicking "Save".

![](../img/datasets-work-with/img2.png)

Dataset as all other catalog objects can be marked with star and commented by all users who have access to this dataset.
Dataset's owner can edit readme (Readme tab) and manage dataset versions (Versions tab).

Also dataset can be created with [kdataset tool](../tools/kdataset.md). This tool allows to create dataset version with only with Name and Publish parameters. Other parameters (Description, Keywords, etc...) can be edited only in UI.

# Update dataset

Dataset info can be updated only in UI.

![](../img/datasets-work-with/img3.png)

"Edit" option is available in dataset's context menu. User can change dataset's Name, Desctiption and Keywords. Identification can not be changed.

User can change dataset's visibility option (Publish/Unpublish option): make dataset published (available for all users) or not (available only for users who can manage datasets in current organization).

Also user can change dataset's picture.

# Delete dataset

Dataset can be deleted both from UI (context menu "Delete") and with [kdataset tool](../tools/kdataset.md).
