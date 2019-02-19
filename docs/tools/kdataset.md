## kdataset
Utility script for dataset management.

Usage: `kdataset <command>`

Available Commands:

 * **bash-completion**: Generates bash completion scripts
 * **delete**:	        Delete specific catalog entity.
 * **list**:		    List catalog entities for the given workspace.
 * **help**:			Help for any kdataset command.
 * **pull**:			Download the data entity archive.
 * **push**:			Push the data within the current directory.
 * **version-delete**:	Delete specific version of the catalog entity.
 * **version-list**:	List versions for the given catalog entity.

Flags:

 * **--config** string           Path to config file. (default ~/.kuberlab/config)
 * **--debug**                   Enable debug level (shortcut for --log-level=debug).
 * **-h**, **--help**            help for kdataset
 * **--insecure**                Enable insecure SSL/TLS connection (skip verify).
 * **--log-level** *string*      Logging level. One of (debug, info, warning, error) (default "info")
 * **--secret** *string*         Kibernetika AI workspace secret (auth method)
 * **-t**, **--token** *string*  Kibernetika AI user token
 * **--type** *entityType*       Choose entityType type for request: \[dataset model] (default dataset)
 * **--url** *string*            Base url to dataset storage.
 * **--version**                 version for kdataset
 * **--workspace** *string*      Kibernetika AI workspace name (auth method)

## kdataset commands

##### delete

Usage: `kdataset delete <workspace> <entity-name>`

Example:
```bash
kdataset delete my-workspace dataset-to-delete
```

##### list

Usage: `kdataset list <workspace>`

Example(listing models):
```bash
kdataset list my-workspace --type model
```

##### pull

Usage: `kdataset pull <workspace> <entity-name>:<version> [-O output-file.tar]`

Flags:

 * **-O**, **--output string**:	Output filename.

Example:
```bash
kdataset pull my-workspace big-dataset:1.0.1
```
**Note**: The command above will create a file named `my-workspace-big-dataset.1.0.1.tar`

##### push

Usage: `kdataset push <workspace> <entity-name>:<version> [flags]`

Flags:

 * **--chunk-size** int:           Chunk-size for scanning (default 1024000 ~ 1MB).
 * **-c**, **--concurrency** int:  Number of concurrent request to server (defaults to CPU cores num).
 * **--create**:		           Create entity in catalog if not exists.
 * **--comment** string:           Comment for the new version
 * **-f**,  **--force**:	       Force uploading regardless warnings.
 * **--publish**                   Newly created dataset will be public. Only used in conjunction with --create.

Example (creating and publishing some dataset):

```bash
kdataset push my-workspace big-dataset:1.0.1 --create --publish
```

##### version-delete

Usage: `kdataset version-delete <workspace> <entity-name>:<version>`

Example (deleting model version):
```bash
kdataset --type model version-delete my-workspace tf-model:1.0.1
```

##### version-list

Usage: `kdataset version-list <workspace> <entity-name>`

Example:
```bash
kdataset version-list my-workspace big-dataset
```

## More Examples:

`kdataset push test-projects cifar-10:1.0.0`

`kdataset push test-projects cifar-10:1.0.0 --create`

`kdataset version-list test-projects cifar-10`

`kdataset pull test-projects cifar-10:1.0.0`

## Installation:

Download the version for your OS from the **kdataset** [release page](https://github.com/kuberlab/pluk/releases)

Uncompress the downloaded tarball.

Copy the **kdataset** utility to the folder pointed to by “PATH” environment” variable

```bash
sudo cp kdataset /usr/local/bin
```

To connect from the ***kdataset*** utility to the **Kibernetika**
application, you need a **Kibernetika** config file at **~/.kuberlab/config**.
If you do not have one, you need to create one.

The configuration values that need to be created are (basically, it is a simple file in YAML format):

```yaml
base_url: https://cloud.kibernetika.io/api/v0.2 # url to access Kibernetika API.
token: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx # your token, which can be obtained from the settings page of the Kibernetika application.
```

Please refer to [kdataset README.md](https://github.com/kuberlab/pluk/blob/master/README.md#cli-reference) for more detailed configuration.

To verify the installation, at first use
`kdataset --version`, to verify that you are executing the right version of utility

Then execute
`kdataset list kuberlab-demo`

And you should see the list of all the demo data sets.


