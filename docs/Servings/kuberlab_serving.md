## kuberlab-serving

This is a document describing the possibilities and parameters of
**kuberlab-serving** tool.

## What is it?

**kuberlab-serving** tool is a generic machine-learning model runner.
Basically, it starts the gRPC server and receives google protobuf messages
(just like `tensorflow_model_server` does) and optionally, it can start
HTTP proxy to that gRPC server, so the requests to the server become much
more easier.

It supports the following machine learning frameworks and formats:

* **TensorFlow**
* **ONNX** (via Intel nGraph)
* **Intel OpenVINO**
* **PyTorch**

Also, it can be run without model and all required logic may be in the
process hooks (see [hooks](kuberlab_serving.md#hooks) section below), for that need to take `null` driver.

**kuberlab-serving** tool is available in *serving* containers:

* **kuberlab/serving:latest** (basic image, doesn't include OpenVINO support)
* **kuberlab/serving/latest-gpu** (includes GPU-related stuff)
* **kuberlab/serving:latest-openvino** (includes OpenVINO)

## CLI interface

Once you have an access to **kuberlab-serving** executable, you are ready to use it.
Let's see the options and flags which can be provided during start.

```
usage: kuberlab-serving [-h] [--driver DRIVER] --model-path MODEL_PATH
                        [--hooks HOOKS] [--option OPTION] [--port <int>]
                        [--http-enable]
                        [--http-server-command HTTP_SERVER_COMMAND]
                        [--http-port HTTP_PORT]
```

optional arguments:

*  **-h, --help** :           show this help message and exit
*  **--driver DRIVER** :       Driver to use in ML serving server.
*  **--model-path MODEL_PATH** : Path to model file or directory.
*  **--hooks HOOKS** : Hooks python file containing preprocess(inputs) and postprocess(outputs) functions.
*  **--option OPTION, -o OPTION** : Additional options specific to driver. format: -o option_name=option_value
*  **--port <int>** :         Port on which server will listen
*  **--http-enable**:         Enables HTTP proxy for gRPC server
*  **--http-server-command HTTP_SERVER_COMMAND** : Command for running http tfservable-proxy
*  **--http-port HTTP_PORT** : Port for http server

## Drivers

This section describes the list of available backends (drivers) and their specific options.

#### TensorFlow

Driver name used in options: **tensorflow**.

Options which are used in TensorFlow driver (may be provided via **-o option_name=option_value**):

* **model_signature**. Used if **--model-path** is a saved-model-dir.
If so, driver extracts provided model_signature from **saved_model.pb**.
Default value is **serving_default** (default constant in tensorflow package).
Example: `-o model_signature=transform`
* **inputs**: Used only if **--model-path** is a .pb graph file. Service will
be using the provided tensor names as an input. Example: `-o inputs=input,prob1`
* **outputs**: Used only if **--model-path** is a .pb graph file. Service will
be using the provided tensor names as an output. Example: `-o outputs=output,embeddings`

Values accessible from processing hooks:

* **graph**: TensorFlow graph
* **sess**: TensorFlow session
* **model_inputs**: dict of tensor inputs, tensor name as a key and tensor as a value
* **model_outputs**: list of output tensor names
* **driver**: TensorFlowDriver object.

#### PyTorch

Driver name used in options: **pytorch**.

Options which are used in PyTorch driver (may be provided via **-o option_name=option_value**):

* **model_class**. **Required**. It is an import path to PyTorch Net class.
Example: `-o model_class=package.module:NetClass`

Values accessible from processing hooks:

* **model**: PyTorch model object
* **model_class**: PyTorch model class
* **driver**: PyTorchDriver object.

#### Intel OpenVINO

Driver name used in options: **openvino**.

Options which are used in Intel OpenVINO driver (may be provided via **-o option_name=option_value**):

* **model_weights**: Path to weights (*.bin*) file. May be used in case weights
file is in another location with *.xml* file
* **device**: The device which should be used for computation. Multiple devices
can be provided so in this case **HETERO** plugin will be used.
Possible values: **CPU**, **MYRIAD**, **FPGA**. Examples:
`-o device=CPU`, `-o device=MYRIAD`, `-o device=CPU,MYRIAD`.
* **flexible_batch_size**: Use variable first dimension in input data. In this
case the network will be executed multiple times. For example, if your network
receive input shape (1, 28, 28) and outputs (1, 10), then **flexible_batch_size**
enables the possibility to pass (N, 28, 28) as an input. Then the serving
output will be (N, 10) accordingly to each input request. Example:
`-o flexible_batch_size=true`

Values accessible from processing hooks:

* **exec_net**: Executable Network object
* **model_inputs**: Input model dict: input name -> input shape
* **model_outputs**: Output name list
* **plugin**: Plugin object (may be used in order to load more networks
in hooks on the same device)
* **driver**: IntelOpenVINODriver object

#### ONNX (Open Neural Network Exchange)

Driver name used in options: **onnx**.

Options which are used in ONNX driver (may be provided via **-o option_name=option_value**):

* **runtime_backend**: Runtime backend used for initilizing backend.
Possible values: *CPU*, *GPU*, *INTERPRETER*, *ARGON*, *NNP*. Default value - **CPU**.

#### Null driver

Driver name used in options: **null**.

This driver is essentially needed only for using in conjunction with hooks.
It provides the possibility to create your own serving logic without a
model at all. The driver itself just returns what it received as an input.

No other specific options are provided.

## Hooks

This section describes the possible ways of writing serving hooks and their capabilities.