## kuberlab-serving

This is a document describing the possibilities and parameters of
**kuberlab-serving** tool.

### What is it?

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

### CLI interface




### Hooks