## Uploading the model

Using **mlboardclient** it is possible to upload the catalog as a model.

Once the client have been initialized, it may be used as the following:

```python
mlboard.model_upload("model-name", "1.0.0-version", "/model-catalog-dir")
```

Full **model_upload** method spec:

```
model_upload(self, model_name, version, path,
             workspace=None, auto_create=True, spec=None)
```

Arguments:

* **auto_create**: if True, then model will be created if there is no such model yet. Defaults to **True**.
* **spec**: Optional model spec dict, it contains model specification used
for starting the model as a serving. If None and this method is called inside
ML project, then **mlboardclient** tries to get spec automatically from the project if it exists.
See about model spec format below.
* **workspace**: Optinal parameter. Must be provided if the method is called outside of ML project.


### Model spec format

Model spec should be dict or corresponding JSON-string. Example is below:

```
{
  "displayName": "Serving",
  "name": "tensorflow-serving",
  "ports": [
    {
      "protocol": "TCP",
      "targetPort": 9000,
      "name": "grpc",
      "port": 9000
    }
  ],
  "command": "kuberlab-serving --port=9000 --model-path=$SRC_DIR",
  "sources": [
    {
      "mountPath": "/src",
      "name": "src"
      "gitRepo": {
        "repository": "https://github.com/kuberlab-catalog/tensorflow"
      }
    }
  ],
  "images": {
    "gpu": "kuberlab/serving:latest-gpu",
    "cpu": "kuberlab/serving:latest"
  },
  "spec": {
    "outFilter": "string",
    "rawInput": true,
    "model": "string",
    "params": [
      {
        "name": "input",
        "type": "bytes"
      }
    ]
  },
  "resources": {
    "accelerators": {
      "gpu": 0
    },
    "requests": {
      "cpu": "100m",
      "memory": "125Mi"
    },
    "limits": {
      "cpu": "1",
      "memory": "4Gi"
    }
  }
}
```

**Note**: `spec` section is needed mostly for the web UI, to pass the data to the serving via web UI.