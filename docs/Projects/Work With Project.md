## Edit project summary.
Use "SUMMARY" tab to add some notice or describe your Project. We are supporting [Markdown](https://en.wikipedia.org/wiki/Markdown) format for Project summary.
![](/img/project/summary-1.png)

![](/img/project/summary-2.png)

## Work with sources
Project requires configured sources for saving model,source code of model,training data...
You can configure all data sources in the "SOURCES" tab and after mount it to tasks or to Project specific UI interface like Jupyter or Tensorboard.
We are supporting following data source type:

* GIT - git repository. GitHub,BitBucket,GitLab,...
* NFS - external network file system that support NFS protocol.
* Cluster Storage - storage attached to your cluster by administrator. See [Cluster Storage](/Resources/Clusters.md).
* Kuberlab Storages - persistent volume from your infrastructure. See [Kuberlab Storage](/Resources/Kuberlab Storage.md).
* S3 Bucket - Storage that used your S3 bucket as data source.

To add new storages or edit old open "SOURCES" tab in the Project.
![](/img/project/storage-1.png)

Fill all required fields:

* Name - data source name
* Sub Path - optional field. Path to mount the directory inside attached file system.
* Mount Path - path inside Project.
* Type - choose one of the data source type

![](/img/project/storage-2.png)

### Git data source.
To connect git source type you need specify following fields:

* Repository - git repository path, like https://github.com/kuberlab-catalog/tensorflow. Also you could use Simple dialog box to specify directory if you have connected git account in the [user setting](/Settings/User.md#Services.md).
* Sub Path - by default content of git repository will be visible in a Project under "MountPath/RepoName". But by specifying Sub Path you can change this behavior. For example if your repository has "src" folder and you want that mount content of this to  "MountPath/" you should set "Sub Path" to "RepositoryName/src".
* Account - must be set if it is private repository or you want to commit changes. It is secret that hold user private data, like access key or deploy key. See [service account management](/Settings/User.md#Service Accounts.md)

![](/img/project/git-source-config.png)

## Task managment
dds
## History
dsdsds
## Log
jkjk
## Status