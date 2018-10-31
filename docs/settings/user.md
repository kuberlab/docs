# User Settings
To change personal info or configure access to external repositories and service account go to settings page.

![](../img/settings/settings.png)

# Repositories
You can add  OAuth based connection to your external git repositories or to your google account. This is required if you are planning to create your own clusters or want to be able to connect your git repositories to your projects as a storage volume.

Following OAuth connections is supported:

* [Github](https://github.com)
* [BitBucket](https://bitbucket.org)
* [Google Cloud](https://cloud.google.com)

# Service Accounts
Used for manage private information such as secrets,keys or password for external resources.

![](../img/settings/settings2.png)

You could add following Service accounts:

* Google - OAuth credentials. Required for creating and provisioning your own [clusters](../resources/clusters.md) on the Google cloud.
* Amazon - AWS access ID and secret key. Required for creating and provisioning your own [clusters](../resources/clusters.md) on the AWS or to connecting [AWS S3 Bucket as data source](../projects/working-with-projects.md#s3-bucket-storage) to your project.
* GIT - Private deploy key or user name and access token. Required for connecting private git repositories as data source to your project. See [Git data source](../projects/working-with-projects.md#git-data-source) for details and [using deploy keys](https://developer.github.com/v3/guides/managing-deploy-keys/#deploy-keys) or using [access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)

# User Token
You can create a personal access token and use it in place of a password for **Kibernetika** API or for CLI tools.

# Delete User
Delete User will allow you to completely remove your user from **Kibernetika** service. This action will delete your account and all data associated with it. <mark>ATTENTION:</mark> Be careful, all your data will be lost after this action!