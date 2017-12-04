## Edit project summary.
Use "SUMMARY" tab to add to add information and additional materials which will describe your Project. We are supporting [Markdown](https://en.wikipedia.org/wiki/Markdown) format for Project summary.
![](/img/project/summary-1.png)

![](/img/project/summary-2.png)

## Work with sources.
Project requires configured data sources for training data, model source code, and results and checkpoints
You can configure all data sources in the "SOURCES" tab and mount it to different Tasks or to Project specific UI interface like Jupyter or Tensorboard.
We are supporting following data source types:

* GIT - git repository. You can connect you GitHub, GitLab or BitBucket account or use any other git server
* NFS - external network file system that support NFS protocol.
* Cluster Storage - storage attached to your cluster by administrator or provided by Kuberlab service. See [Cluster Storage](/Resources/Clusters.md).
* S3 Bucket - Storage that used your S3 bucket as data source.

To add new storages or edit old open "SOURCES" tab in the Project.
![](/img/project/storage-1.png)

Configuration:

* Name - data source name. Required
* Sub Path - optional field. Path to mount the directory inside attached file system.
* Mount Path - path inside Project. Required
* Type - choose one of the data source type, Required

![](/img/project/storage-2.png)

### Git data source.
To connect git data source you need to specify following fields:

* Repository - git repository path, like https://github.com/kuberlab-catalog/tensorflow. You can use dialog box to specify repository if you have connected git account in the [user setting](/Settings/User.md#Services).
* Sub Path - by default content of git repository will be visible in the Project under "MountPath/RepoName". By specifying Sub Path you can change this behavior. For example if your repository has "src" folder and you want to mount its content to  "MountPath/" you should set "Sub Path" to "RepositoryName/src".
* Account - Account must be set for private repository if you want to be able to commit changes. You need to provide secret that hold user private data, like access key or deploy key. See [service account management](/Settings/User.md#Service Accounts)

![](/img/project/git-source-config.png)

### NFS data source.
External network file system that support NFS protocol. To connect NFS source type you need specify following fields:

* Server - address of your NFS.
* Path - NFS internal path.
* Sub Path - Path to data inside NFS. For example if your want mount directory "/mypath/data" from NFS  to  directory "/MountPath/data", you should set mount path to "/MountPath/data" and Sub Path to "/mypath/data"

![](/img/project/nfs-storage.png)

### Cluster Storage.
Storage attached to shared cluster or cluster from your infrastructure. If there are no available cluster storage for you, contact to your administrator or support.
To Connect Cluster storage you should specify only one of available for you cluster storage. See [Cluster Storage](/Resources/Clusters.md) for information about creating an management  this data source type.

<mark>ATTENTION</mark>: following rules is applied for Sub Path variable:

* If Sub Path begins from '/' symbol then data will be visible for all project in your organization and you can mount this data to other projects on the same organization. 
* If path begins from '/shared/' then data  will be visible to everyone who have access to the same storage, even in another organization.
* Otherwise data will be visible only inside your project.

![](/img/project/cluster-storage.png)

### Kuberlab Storage.

### S3 Bucket.

![](/img/project/s3-storage.png)

## Task managment
dds
## History
dsdsds
## Log
jkjk
## Status
