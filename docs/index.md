# Quick Start Guide

## Kuberlab Basics

This tutorial provides a step-by-step guide to the initial setup of the Kuberlab Application Management Platform, which will help you run a sample application using a template from the KuberLab catalogue. This will also demonstrate the basic forms of:

* Infrastructure Management

* AI Application Management

* Application Deployment

The steps are listed in the order they are to be performed.


## Kuberlab Registration

You must have a Kuberlab account to use the platform. Once your account is created, you will be able to log into our system and connect your source code and cloud service accounts, so Kuberlab can perform all cloud automation on your behalf.

1. Go to the web page: [https://go.kuberlab.io](https://go.kuberlab.io)

2. Sign up with your email address and other required information ![](img/signup2.png)

3. A confirmation email will be sent to you within 24 hours. Follow the instructions in this email to complete your registration. If you do not receive the e-mail message from the address "noreply@kuberlab.io" within 24 hours of initial registration, please check the Spam folder. If you have not received the confirmation e-mail, please contact [support@kuberlab.com](mailto:support@kuberlab.com)


### [Optional] Source Account Registration

If you wish to run your own model or application source code, but do not have a source account to store and host it, you can create one with any of the following services at their respective sites:  

Github: [https://github.com/](https://github.com/)  
Gitlab: [https://gitlab.com/](https://about.gitlab.com/)  
Bitbucket: [https://bitbucket.org/](https://bitbucket.org/product)  

If you already have a source account, you can connect it to the Kuberlab service:

1. After logging in, go to ‘Settings’ page (click your user name in the upper right, and then ‘Settings’). You can go to the page directly using this link: [https://go.kuberlab.io/settings/my](https://go.kuberlab.io/settings/my). ![](img/image_1.png)

2. Under ‘Services’, add and configure the source account that contains your application or model source code. ![](img/image_2.png)


### [Optional] Cloud Account Registration

Kuberlab provides you a shared cluster to run your applications during your trial period. You can also configure a local Kubernetes cluster. Hence a cloud service account registration is optional. If you do not wish to use the shared cluster, or if your trial period is over, you will need to either configure a local cluster, or use a cloud service, and connect this to the Kuberlab service.

If you need a cloud service account to run your cluster, you can create one with the following services at their respective sites:  
Google: [https://cloud.google.com/](https://cloud.google.com/)  
AWS: [https://aws.amazon.com/](https://aws.amazon.com/)  

To configure your cluster in the Kuberlab service:
1. Go the the 'Settings' page as before (see Source Account Registration).

2. Under ‘Service Accounts’, add and configure the cloud service account where you will run your cluster. Currently Kuberlab supports Google Cloud, AWS, and local Kubernetes clusters.
![](img/image_3.png)

## [Optional] Infrastructure Creation

If you are trying out the Kuberlab service with the provided example templates and the shared cluster (free trial period only), you do not need to follow this step. If you wish to connect your own source code and/or your own cluster to the Kuberlab service, you need to create new infrastructure.

To create new infrastructure, click on the 'Resources' tab in your workspace, and then click the button on the right labeled 'Create new infrastructure'. Fill in the fields. You can use the 'Expand' button to choose the repository type, and then be prompted by the system to help you choose the remaining fields by showing you the available selections.

Click 'Save' to save your infrastructure details.

## Project Creation

Before you can do anything with an application, you need to create a project.

1. From the main tab (click ‘Kuberlab’ at the top left), click the button on the right labeled 'Create new Project'.
![](img/image_4.png)

2. From the list of sample templates shown, choose the most relevant (click the 'Install' button)

3. Choose your cluster. If you have created infrastructure with the optional step above, this is where you can choose your own cluster. Otherwise, you will choose the default shared cluster 'testshare' here. Click 'Next'.

4. Name your application. Most users will leave the default name as is here. Click 'Next'.

5. Choose the versions of various tools you need. Most users will use the default values here. Click 'Next'.

6. The last step of template installation shows the configuration. There is not need to modify anything here. Click 'Install'.

This will install the template and take you to the project screen.

## Running your Project

In the project screen, you will see several tabs. You can run template code from either the 'Jupyter' or the 'Tasks' tab. The former allows you to step through the code and read the notes, hence is the easier method. The latter is the tab that is used for the production flow, and allows you to define several tasks that can be run either serially or in parallel, and any number of combinations of both.

The 'Sources' tab allows you to navigate the directory structure and look at all the template files. If you wish to connect your own sources, you can do this here, by adding a new source path.

The 'History' tab contains a list of all the jobs you have run.

'Logs' shows the details of all the tasks started.

'Status' shows the current status of all tasks you have started.

You can monitor your application from the 'Metrics' and 'Tensorboard' tabs.

To add tools and frameworks packages from the open source community, use the 'Lib' tab.
