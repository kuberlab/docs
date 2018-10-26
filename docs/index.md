# Quick Start Guide

## Kibernetika Basics

This tutorial provides a step-by-step guide to the initial setup of the  **Kibernetika Machine Teaching Platform**, which will help you run a sample application using a template from the catalogue. This will also demonstrate the basic forms of:

* Infrastructure Management

* AI Application Management

* Application Deployment

The steps are listed in the order they are to be performed.


## Kibernetika Registration

You must have an account to use **Kibernetika**. Once your account is created, you will be able to log into our system and connect your source code and cloud service accounts, so it can perform all cloud automation on your behalf.

1. Go to the web page: [https://cloud.kuberlab.io](https://cloud.kuberlab.io)

2. Sign up with your email address and other required information 

![](img/quickstart/login.png)

3. A confirmation email will be sent to you within 24 hours. Follow the instructions in this email to complete your registration. If you do not receive the e-mail message from the address "noreply@kibernetika.ai" within 24 hours of initial registration, please check the Spam folder. If you have not received the confirmation e-mail, please contact [support@kibernetika.ai](mailto:support@kibernetika.ai)


### [Optional] Source Account Registration

If you wish to run your own model or application source code, but do not have a source account to store and host it, you can create one with any of the following services at their respective sites:  

Github: [https://github.com/](https://github.com/)  
Gitlab: [https://gitlab.com/](https://about.gitlab.com/)  
Bitbucket: [https://bitbucket.org/](https://bitbucket.org/product)  

If you already have a source account, you can connect it to the Kibernetika service:

1. After logging in, go to ‘Settings’ page (click your user name in the upper right, and then ‘Settings’). You can go to the page directly using this link: [https://cloud.kuberlab.io/settings/my](https://cloud.kuberlab.io/settings/my).

![](img/quickstart/settings.png)

2. Under ‘Repositories’, add and configure the source account that contains your application or model source code. 

![](img/quickstart/add_repo.png)


### [Optional] Cloud Account Registration

**Kibernetika** provides you a shared cluster to run your applications. You can also configure to use your local Kubernetes cluster. Hence a cloud service account registration is optional. If you do not wish to use the shared cluster you will need to either configure a local cluster, or use a cloud service, and connect this to kibernetika.ai service.

If you need a cloud service account to run your cluster, you can create one with the following services at their respective sites:  
Google: [https://cloud.google.com/](https://cloud.google.com/)  
AWS: [https://aws.amazon.com/](https://aws.amazon.com/)  

To configure your cluster in the **Kibernetika** service:
1. Go the the 'Settings' page as before (see Source Account Registration).

2. Under ‘Service Accounts’, add and configure the cloud service account where you will run your cluster. Currently Kibernetika supports Google Cloud, AWS, and local Kubernetes clusters.

![](img/quickstart/add_service.png)

## Project Creation

Before you can do anything with an application, you need to create a project.

1. If you want to run one of the tutorials in the catalogue, you can create a tutorial project. In this case, click on the 'Catalog' button at the top. If you however want to build your own code, or use your own from your connected repository, click on your workspace from the main tab (click ‘kibernetika.ai’ at the top left) and then click the button on the right labeled 'Create new Project'.

![](img/quickstart/new_project.png)

2. From the list of tutorials, or sample templates shown, choose the most relevant (click the 'Install' button). If you are choosing a tutorial, the 'tensorflow-tutorial-01' is a good place to start - click "Install to My", and then choose your workspace in the wizard that pops up.

![](img/quickstart/proj_sample_templates.png)

3. Choose your cluster. If you have created infrastructure with the optional step above, this is where you can choose your own cluster. Otherwise, you will choose the default shared cluster 'testshare' here. Click 'Next'.

![](img/quickstart/choose_cluster.png)

4. Name your application. Most users will leave the default name as is here. Click 'Next'.

![](img/quickstart/name_app.png)

5. Choose the versions of various tools you need. Most users will use the default values here. Click 'Next'.

![](img/quickstart/version_select.png)

Scroll down to access additional configurations

![](img/quickstart/version_select2.png)

![](img/quickstart/version_select3.png)

6. The last step of template installation shows the configuration. There is no need to modify anything here. Click 'Install'.

![](img/quickstart/config.png)

This will install the template and take you to the project screen.

## Running your Project

In the project screen, you will see several tabs. You can run your code from the 'Tasks' tab. This tab is used for the production flow, and allows you to define several tasks that can be run either serially or in parallel, and any number of combinations of both.

The 'Sources' tab allows you to navigate the directory structure and look at all the template files. If you wish to connect your own sources, you can do this here, by adding a new source path.

The 'History' tab contains a list of all the jobs you have run.

'Logs' shows the details of all the tasks started.

'Status' shows the current status of all tasks you have started.

You can monitor your application from the 'Metrics' and 'Tensorboard' tabs.

To add tools and frameworks packages from the open source community, use the 'Lib' tab.

![](img/quickstart/project.png)

The 'Jupyter' allows you to step through the code and read the notes, hence is the easier method. 

![](img/quickstart/project_jupyter.png)



