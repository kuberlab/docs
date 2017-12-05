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
Every project contains number of task that user can scheduler for execution. All base project templates and tutorial from Kuberlab catalog already have number preconfigured that. You can edit those tasks, remove it or create new one.

![](/img/project/tasks1.png)

![](/img/project/tasks2.png)

Tasks have one or more resources. Resource is execution entity of the task. Multiple resources inside tasks generally required for distributed training. Also every resource can has any number of replicas.  Every resource replica will be executed inside container during task execution and they could communicate to each other through TCP or UDP protocol. Following environment variables is available inside execution containers:

| Variable | Purpose | Example values |
| ------------ | ------------- | ------------ |
| GPU_COUNT | Number GPU available for replica  | 0,1, ...,n |
| PYTHONPATH | Location of users python library  | $LIB_DIR:.... |
| REPLICA_INDEX | Index of current replica. Useful for distributed training | 1,2,... |
| upper_case({ResourceName})_NODES | comma separated list of dns addresses resource replicas | T1-R1-0-0.R1-0,T1-R1-0-1.R1-0,... (where T1 task name,R1 resource name) |
| BUILD_ID | Id of current task run | 1,2...,n |
| upper_case({SourceName})_DIR | Mount point for Source with name 'SourceName' | /workspace/src |

Following parameter used for specify task execution:

| Field | Purpose | Example values |
| ------------ | ------------- | ------------ |
| Execution directory | Directory to start user command | For example $SRC_DIR |
| Timeout | Time to wait compute resource | 300 |
| Execution command | Command to start compute process | python styles.py --job_name=worker --train_dir=$TRAINING_DIR/$BUILD_ID  --task_index=$REPLICA_INDEX --ps_hosts=$PS_NODES --worker_hosts=$WORKER_NODES |
| Resources | Specify minimum and maximum compute resources requirements | Requires at least CPU=100m, Memory=62Mi, but no more than CPU=4000m, Memory=8Gi and GPU=1 for each resource replica | 
| Environment variables | User defined environment variables | MY_VARIABLE = value |
| Images | Define container images that will be used for cpu and gpu | (tensorflow/tensorflow:1.2.0,tensorflow/tensorflow:1.2.0-gpu) |
| Default volume mapping | Useful to mount all sources to container as they are defined in the sources | true or false |
| Default mount path | add some prefixed prefix to mount points for all sources |
| Volumes | specify custom sources mounting to container | (data,subfolder,/mynewfoler/andsubfoler) |
| Node Allocator | For public clouds only. Template to allocate new compute resource on the public cloud if there isn't resource available | template name from your cluster configuration |


# History
Coming soon.
# Log
Coming soon.
# Status
Coming soon.
# Integrate Project to your workflow engine
Coming soon.
