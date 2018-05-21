##Catalogs

Catalog is a major elemnt of KuberLab solution. Place where you can find pre-packaged datasets, pre-trained models, project templates and examples. 

KuberLab Catalog is prepopulated with selected open datasets and open source models. Users also can publish their own content in the KuberLab Catalog. 

Globaly accessible KuberLab Catalog is accessed by the whole KuberLab community of users and organizations. Catalog in the user workspace is private to the users and catalogs in the organization workspace belong to the organization and accessible only by users in that organization. 

Every catalog has four sections. <b>Applications, Services, Models, Datasets</b>

###Applications  

Application catalog contain application and project templates. 

Project templates are the starting point of any project. Each project contain everything needed to create starting developemnt environment for specific machine learning framework. KuberLab provides templates for every major machine learning like Tensorflow, PyTorch, MXNet and many more. If user or organization has special requirements for their environmet, custom template can be build and deployed using provided instruction or request can be placed to KuberLab support. 

Application templates are very similar to project templates, but contain deployment of the whole application with source code, data and developemnt environment. Those templates are used primary to create tutorials and other tipes of educational and demo content.

###Services (Charts) 

Service catalog, sometimes named as chart catalog, is the repository for Kubernetes charts, defining deployments of microservices to the Kubernetes cluster. Any Kubernetes application or services can be deployes in this way to KuberLab environment. That capability allow KuberLab to host not only ML/DL models, but also the clients for those models. 

###Models

Models catalog provide several important functionalities. Storage and acceess to the model bits, versioning of the models,remote deployment, and model serving to serve models in the cloud.

There are two types of models you can find in KuberLab catalog. We placed several popular open source pre-trained models i the catalog. Pre-trained models can be easily accessed from the projects and users can developed their own models based on the ones in the catalog. 

Another type of models are developed and saved in the catalog from the user projects. KuberLab public and privarte catalogs provide searving capabilities. The model developed in the project can be serverved using REST or gRPC API.

###Datasets

Recognizing the importance of the data, and complexity of the data processing, KuberLab implemented the ‘Dataset’ object. This object can be loaded, versioned, accessed, and commented on. The Dataset object can be published in the KuberLab public catalog or it can be kept in a private workspace as well. KuberLab also provides a number of open publicly available datasets as part of the public catalogs, so that using them is convenient and does not require further slow data downloads.

To use the Dataset object in the KuberLab project, a user needs to add ‘Dataset’ as a source in the project, and it will become available to the Jupyter Notebook as well as the Python or R execution environments.

For loading of the new dataset see [Dataset Usage](/Datasets/usage.md) for details.










