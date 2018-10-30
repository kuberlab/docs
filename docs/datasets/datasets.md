## Data
Data is the reason why analytics exists, and why we do machine learning. Without data, there is no need for any deep learning models. Since models exist only for processing and analyzing the data, the following observations about the data are true:

Data needs to be validated and secure. Without this, the results of models could be invalid, or worse, even malicious.

Model training is extremely time-consuming, since it happens with large amounts of data. If the data is properly pre-processed, this operation can significantly speed up the model training and increase the accuracy of the resulting model.

Data changes constantly, which means that the model will need to be re-trained regularly on a different version of the data set.

To generate repeatable results in model prediction, the operation needs to be done with the same data set.

## Dataset
Recognizing the importance of the data, and complexity of the data processing, **Kibernetika** implemented the Dataset object. This object can be loaded, versioned, accessed, and commented on. The Dataset object can be published in the **Kibernetika** public catalog or it can be kept in a private workspace as well. **Kibernetika** also provides a number of open publicly available datasets as part of the public catalogs, so that using them is convenient and does not require further slow data downloads.

To use the Dataset object in the **Kibernetika** project, a user needs to add ***Dataset*** as a source in the project, and it will become available to the Jupyter Notebook as well as the Python or R execution environments.



