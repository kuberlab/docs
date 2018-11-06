# python-mlboardclient

[![Pypi](https://img.shields.io/badge/pypi-python--mlboardclient-green.svg)](https://pypi.python.org/pypi/python-mlboardclient)

Python library for interacting ml-board component. Basically it can
manipulate with current project, it's tasks and servings. Also it provides
the API for datasets and models.

## Installation

### From PyPi

```bash
pip install python-mlboardclient
```

### From github (fresh master branch)

```bash
pip install 'git+https://github.com/kuberlab/python-mlboardclient.git'
```

## Usage

```python
from mlboardclient.api import client

# Default url is http://mlboard-v2.kuberlab:8082/api/v2
# No need to pass any url if instantiate client inside ml-project (Jupyter/Task)
ml = client.Client()
# Get current project object
app = ml.apps.get()
# <App name=21-facenet-openvino55 revision=aba73d27564106a45d9439856c1856d562d9219f>

# Get tasks from config
app.tasks
#[<Task name=align-images build=None status=undefined>,
# <Task name=train-classifier build=None status=undefined>,
# <Task name=validate-classifier build=None status=undefined>,
# <Task name=pipeline build=None status=undefined>,
# <Task name=model-converter build=None status=undefined>]
task = app.tasks[0]

# Start & wait task
task = task.start()
# <Task name=align-images build=4 status=Starting>

# ... wait some time and refresh task
task.refresh()
# <Task name=align-images build=4 status=Running>

# ... or wait task until it completed:
task.wait()
# <Task name=align-images build=4 status=Succeeded>

# Get tasks from API
app.get_tasks()
#[<Task name=validate-classifier build=1 status=Failed>,
# <Task name=train-classifier build=2 status=Failed>,
# <Task name=model-converted build=3 status=Failed>,
# <Task name=align-images build=4 status=Succeeded>]
```

### Model upload

```python
    ml.model_upload('my-model', '1.0.0', '/model/dir')
    # If the model uploading is not executing in scope of project task,
    # need to specify workspace explicitly:
    ml.model_upload(
        'my-model',
        '1.0.0',
        '/model/dir',
        workspace='demo',
    )

    # Wait until model is being uploaded.
```
