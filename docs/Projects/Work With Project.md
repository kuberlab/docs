# Edit project summary
Use "SUMMARY" tab to add information and additional materials which will describe your Project. We are supporting [Markdown](https://en.wikipedia.org/wiki/Markdown) format for Project summary.
![](/img/project/summary-1.png)

![](/img/project/summary-2.png)

# <a name="source"></a>Working with sources
Project requires configured data sources for training data, model source code, results and checkpoints
You can configure all data sources in the "SOURCES" tab and mount it to different Tasks or to specific Project component like Jupyter or Tensorboard.
We are supporting following data source types:

* GIT - git repository. You can connect you GitHub, GitLab or BitBucket account or use any other git server
* NFS - external network file system that support NFS protocol.
* Cluster Storage - storage attached to your cluster by administrator or provided by Kuberlab service. See [Cluster Storage](/Resources/Clusters.md).
* S3 Bucket - Storage that used your S3 bucket as data source.

To add new storages or edit old open "SOURCES" tab in the Project.
![](/img/project/storage-1.png)

Configuration:

* Name - data source name. Valid name must be 63 characters or less and must begin and end with an lower case alphanumeric character ([a-z0-9]) with dashes (-) and lower case alphanumerics between. 
* Sub Path - optional field. Path to mount the directory inside attached file system.
* Mount Path - path inside Project. Required
* Type - choose one of the data source type, Required

![](/img/project/storage-2.png)

# <a name="git-data-source"></a>Git data source
To connect git data source you need to specify following fields:

* Repository - git repository path, like https://github.com/kuberlab-catalog/tensorflow. You can use dialog box to specify repository f you have connected git account in the [user setting](/Settings/User.md#repositories).
* Sub Path - by default content of git repository will be visible in the Project under "MountPath/RepoName". By specifying Sub Path you can change this behavior. For example if your repository has "src" folder and you want to mount its content to  "MountPath/" you should set "Sub Path" to "RepositoryName/src".
* Account - Account must be set for private repository if you want to be able to commit changes. You need to provide secret that hold user private data, like access key or deploy key. See [service account management](/Settings/User.md#service-accounts)

![](/img/project/git-source-config.png)

# <a name="nfs-data-source"></a>NFS data source
External network file system that support NFS protocol. To connect NFS source type you need specify following fields:

* Server - address of your NFS.
* Path - NFS internal path.
* Sub Path - Path to data inside NFS volume. For example if your want to mount directory "/mypath/data" from NFS  to  directory "/MountPath/data", you should set mount path to "/MountPath/data" and Sub Path to "/mypath/data"

![](/img/project/nfs-storage.png)

# <a name="cluster-data-source"></a>Cluster Storage
Storage attached to shared cluster or cluster from your infrastructure. If you do not have cluster storage configured, contact  administrator or support.
To Connect Cluster storage you should specify one of the available cluster storage. See [Cluster Storage](/Resources/Clusters.md) and [Kuberlab Storage](/Resources/Kuberlab Storage.md) for information about creating and management  this data source type.

<mark>ATTENTION</mark>: following rules are applied to Sub Path variable:

* If Sub Path begins from '/' symbol then data will be visible for all projects in your organization and you can share this data to other projects belonging to the same organization. 
* If path begins from '/shared/' then data  will be visible to everyone who have access to the same storage volume, even from another organization.
* Otherwise data will be visible only inside your project.

![](/img/project/cluster-storage.png)

# <a name="s3-data-source"></a>S3 Bucket
Storage that allows to work with S3 bucket data. To connect S3 source type you need specify following fields:

* Server - address of your S3 server. Leave it empty for Amazon S3.
* Bucket - bucket name.
* Account - Secret that holds user private credentials that will be used for S3 connection. See [service account management](/Settings/User.md#service-accounts)

![](/img/project/s3-storage.png)

# Task management
Coming soon.
# History
Coming soon.
# Log
Coming soon.
# Status
Coming soon.
