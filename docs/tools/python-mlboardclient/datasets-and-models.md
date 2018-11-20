## Datasets and models

This section describes data entities API (datasets and models).

**python-mlboardclient** allows to manage datasets and models: in this case
mlboardclient acts as a thin layer to another CLI - [kdataset](../kdataset.md).

### Managing datasets and models

Once the **mlboardclient** is initialized, it can be used to leverage datasets
(for examples below, instance of **mlboardclient** is in **mlboard** variable)

**Note**: All methods below used almost identically for either a **dataset**
or a **model**. To make call for the **model**, pass argument `type='model'`
instead of `type='dataset'` which is used by default.

#### List datasets (or models)

*def list(self, workspace, type='dataset')*

Lists datasets for the given workspace.

**Note:** If inside the project, it is possible to take workspace name from
environment variable **WORKSPACE_NAME**.

Examples:
```python
datasets = mlboard.datasets.list('my-workspace', type='dataset')
print(datasets)
```

```python
import os

datasets = mlboard.datasets.list(os.environ['WORKSPACE_NAME'], type='dataset')
```

#### List version for specific dataset (or model)**

*def version_list(self, workspace, name, type='dataset')*

Lists versions for the given catalog entity.

**Note:** If inside the project, it is possible to take workspace name from
environment variable **WORKSPACE_NAME**.

Example:
```python
v_list = mlboard.datasets.version_list('my-workspace', 'my-dataset', type='dataset')
print(v_list)
```

#### Pull (download) dataset (or model)

*def pull(self, workspace, name, version, to_dir, type='dataset', file_name=None):*

Downloads the data entity tar archive to the specified location.

If `file_name` is *None*, then entity is downloaded to file named `<workspace>-<dataset>.<version>.tar`.
If `to_dir` is empty, then current working directory is used.

Example:
```python
mlboard.datasets.pull('my-workspace', 'my-dataset', '1.0.0', '', type='dataset')
```

#### Push (upload) dataset (or model)

*def push(self, workspace, name, version, from_dir,
          type='dataset', create=False, publish=False, force=False,
          chunk_size=None, concurrency=None, spec=None):*

Push the data within the specified directory.

* If `file_name` is *None*, then entity is downloaded to file named `<workspace>-<dataset>.<version>.tar`.
* If `from_dir` is empty, then current working directory is used.
* If `create` is *True*, then entity will be created if not exists.
* If `publish` is *True*, then entity will be public when created.
* If `force` is *True*, then entity will be created regardless some warnings.

* `chunk_size` is used to specify chunk size for every file in dataset (default `1024000`)
* `concurrency` is used to specify number of concurrent connections (defaults to `<cores_num * 2>`)
* `spec` used only if pushing a **model**. It is a dict of model spec for serving (or compatible json-string). The client
automatically picks up a spec from ML project if any exists. See more details at [Upload a model](upload-model.md).

Example:
```python
mlboard.datasets.push('my-workspace', 'my-dataset', '1.0.0', '/model/path', type='dataset')
```

#### Delete dataset (or model)

*delete(self, workspace, name, type='dataset')*

Deletes specific catalog entity.

Example:
```python
mlboard.datasets.delete('my-workspace', 'my-dataset')
```

#### Delete version of dataset (or model)

*def version_delete(self, workspace, name, version, type='dataset')*

Delete specific version of the catalog entity.

Example:
```python
mlboard.datasets.version_delete('my-workspace', 'my-dataset', '1.0.0')
```




