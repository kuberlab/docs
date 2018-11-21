## Dive into tasks

This section describes nuances and details of working with tasks API in
**mlboardclient**.

### Working with raw task config

Task `config` field contains task configuration including resources config.
Task config can be rewritten before start using:

#### task.apply_env(envs)

It adds/modifies environment variables for task resources.

envs parameter must be a list containing env var specs as following:
ENV_VAR=VALUE

Example:
```python
task.apply_env(['MY_VAR=MY-VAL', 'SOME_VAR=expression=22'])
```
In the example above variable 'SOME_VAR'
will be assigned value 'expression=22'.

#### task.apply_resource_overrides()

Overrides resource-specific config values for given task.

Resource override spec format:
`<resource-name>.<param>=<value>`
or
`<resource-name>.<key>.<nested-key>=<value>`

It is allowed to pass '*' as resource name: override will be applied
to all resources:
`*.<key>=<value>`

Examples:
```python
task.apply_resource_overrides([
  '*.resources.requests.cpu=1000m',
  '*.resources.requests.memory=1Gi'
])
```
```python
task.apply_resource_overrides(['worker.replicas=3'])
```

#### Passing raw arguments dict

Also it is possible to pass additional command arguments as dict. For doing so,
`args` key may be used. All arguments passed in `args` in form of dict, e.g.
`{"var": "val", "arg2", "val2"}` will be appended to execution command as `--var val --arg2 val2`:

```
>>> task.config['resources'][0]['command']
'python my_script.py'
>>> task.config['resources'][0]['args'] = {
...   'var1': 'val', 'batch-size': 23, 'test_arg': 12.2
... }
>>> task.start()
>>> task.config['resources'][0]['command']
'python my_script.py --batch-size 23 --test_arg 12.2 --var1 val'
```

If `args` is a string, then it is appended directly as a string, e.g:

```
>>> task.config['resources'][0]['command']
'python my_script.py'
>>> task.config['resources'][0]['args'] = '--my-super-arg 42; echo "Done!"'
>>> task.start()
>>> task.config['resources'][0]['command']
'python my_script.py --my-super-arg 42; echo "Done!"'
```

### Serving from task and checkpoint variable

When a task completes, it is possible to start a serving job from this task.
For doing so, the form requires model path (a place where the model located)
to run the serving. In order to automate passing model path to the serving job
there is a couple of variables which may be exported in task (via `update_task_info()`
and then further be used in serving form from task.

Serving job accepts the following variables for passing the path:

* checkpoint_path
* model_path

**Example:**

Assuming the task generates a model at `$TRAINING_DIR/model`, the script will be:

```
import os
from os import path
from mlboardclient.api import client

mlboard = client.Client()
data = {
    "model_path": path.join(os.environ['TRAINING_DIR'], 'model')
}
mlboard.update_task_info(data)
```

After that, go to the **Jobs** tab in the UI, find this task, click **`...`**
and then **`Serve`**.

> **`Note`**: For picking up the variable, the execution command must refer the variable
> as usual in a bash script, i.e. **$model_path**

> **`Note 2`**: For better experience, project config should have already prepared
> serving configuration and an execution command which uses needed variable, e.g.
> TensorFlow standard template uses **$checkpoint_path**: [gitlab.kuberlab.io/kuberlab/tensorflow](http://gitlab.kuberlab.io/kuberlab/tensorflow/blob/master/ml-templates/config.yaml#L190)