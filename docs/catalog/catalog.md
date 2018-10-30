##Catalogs

Catalog is a major elemnt of **Kibernetika Machine Teaching Platform**. Place where you can find pre-packaged datasets, pre-trained models, project templates and examples. 

**Kibernetika** catalog is prepopulated with selected open datasets and open source models. Users also can publish their own content in the catalog. 

Globaly accessible catalog is accessed by the whole **Kibernetika** community of users and organizations. Catalog in the user workspace is private to the users and catalogs in the organization workspace belong to the organization and accessible only by users in that organization. 

Every catalog has four sections. <u>Applications, Services, Models, Datasets</u>

###Applications  

Application catalog contain application and project templates. 

Project templates are the starting point of any project. Each project contain everything needed to create starting developemnt environment for specific machine learning framework. **Kibernetika** provides templates for every major machine learning like Tensorflow, PyTorch, MXNet and many more. If user or organization has special requirements for their environmet, custom template can be build and deployed using provided instruction or request can be placed to **Kibernetika** support. 

Application templates are very similar to project templates, but contain deployment of the whole application with source code, data and developemnt environment. Those templates are used primary to create tutorials and other tipes of educational and demo content.

###Services (Charts) 

Service catalog, sometimes named as chart catalog, is the repository for Kubernetes charts, defining deployments of microservices to the Kubernetes cluster. Any Kubernetes application or services can be deployes in this way to **Kibernetika** environment. That capability allow **Kibernetika** to host not only ML/DL models, but also the client applications for those models. 

###Models

Models catalog provide several important functionalities. Storage and acceess to the model bits, versioning of the models,remote deployment, and model serving to serve models in the cloud.

There are two types of models you can find in the catalog. We placed several popular open source pre-trained models there. Pre-trained models can be easily accessed from the projects and users can developed their own models based on the ones in the catalog. 

Another type of models are developed and saved in the catalog from the user projects. **Kibernetika** public and privarte catalogs provide searving capabilities. The model developed in the project can be serverved using REST or gRPC API.

###Datasets

Recognizing the importance of the data, and complexity of the data processing, **Kibernetika** implemented the <u>‘Dataset’</u> object. This object can be loaded,versioned, accessed, and commented on. The Dataset object can be published in the public catalog or it can be kept in a private. **Kibernetika** provides a number of open, publicly available datasets as part of the public catalogs, so that using them is convenient and does not require further data downloads.

To use the <u>Dataset</u> object in the project, a user needs to add <u>Dataset</u> as a volume in the project storage tab or during the project configuration, and it will become available to the Jupyter Notebook as well as the Python or R execution environments.

For loading of the new dataset see [Dataset Usage](../datasets/usage.md) for details.










