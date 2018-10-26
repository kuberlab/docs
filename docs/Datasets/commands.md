## kdataset
Utility script for data set management.

Usage: kdataset \[command]

Available Commands:
 * **dataset-delete**:	Delete specific dataset.
 * **dataset-list**:		List datasets for current workspace.
 * **help**:			Help for any kdataset command.
 * **pull**:			Download the dataset archive.
 * **push**:			Push the data set within current directory.
 * **version-delete**:	Delete a specific version of the data set.
 * **version-list**:		List all versions for the current data set.

Flags:
 * **--config** string      Path to config file (default "~/.kuberlab/config")
 * **--debug**              Enable debug level (shortcut for --log-level=debug).
 * **-h**, **--help**       help for kdataset
 * **--insecure**           Enable insecure SSL/TLS connection (skip verify).
 * **--log-level** string   Logging level. One of (debug, info, warning, error) (default "info")
 * **--type** entityType    Choose entityType type for request: [dataset model] (default dataset)
 * **--url** string         Base url to dataset storage.
 * **--version**            version for kdataset

## kdataset commands

##### dataset-delete

Usage: ***kdataset dataset-delete*** <i>workspace dataset-name [flags]</i>

##### dataset-list

Usage: ***kdataset dataset-list*** <i>workspace [flags]</i>

##### pull

Usage: ***kdataset pull*** <i>workspace dataset-name:version [-O output-file.tar]</i> [flags]

Flags:
 * -h, --help:		help for pull.
 * -O, --output string:	Output filename.

##### push

Usage: ***kdataset push*** <i>workspace dataset-name:version [flags]</i>

Flags:
 * --chunk-size int:      Chunk-size for scanning (default 512000).
 * -c, --concurrency int: Number of concurrent request to server (default 8).
 * --create:		      Create dataset in cloud-dealer if not exists.
 * --comment string:      Comment for the new version
 * -f,  --force:	      Force dataset uploading regardless warnings.
 * -h, --help:		      help for push.
 * --publish              Newly created dataset will be public. Only used in conjunction with --create.
 * -w, --websocket:	      Use websocket for connecting to server. Decreases the number of
requests.

##### version-delete

Usage: ***kdataset version-delete*** <i>workspace dataset-name:version [flags]</i>

Flags:
  -h, --help:	help for version-delete.

##### version-list

Usage: ***kdataset version-list*** <i>workspace dataset-name [flags]</i>

Flags:
  -h, --help:	help for version-list.

## Examples:

kdataset push test-projects cifar-10:1.0.0

kdataset push test-projects cifar-10:1.0.0 --create

kdataset version-list test-projects cifar-10

kdataset pull test-projects cifar-10:1.0.0

## Installation:
Download the version for your OS from the **kdataset** release page

https://github.com/kuberlab/pluk/releases 

Uncompress the downloaded tarball.

Copy the **kdataset** utility to the folder pointed to by “PATH” environment” variable

```bash
sudo cp kdataset /usr/local/bin
```

To connect from the ***kdataset*** utility to the **Kibernetika** application, you need a **Kibernetika** config file at “~/.kuberlab/config”. If you do not have one,you need to create one.

The configuration values that need to be created are:

base_url: 	https://dev.kuberlab.io/api/v0.2 - url to access **Kibernetika** API.

username: 	info@kibernetika.ai - your username.

token: 		xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx - your token, which can be 
obtained from the `settings` page of the KuberLab application.

To verify the installation, at first use
`kdataset --version`, to verify that you are executing the right version of utility

Then execute
`kdataset dataset-list kuberlab-demo`

And you should see the list of all the demo data sets.


