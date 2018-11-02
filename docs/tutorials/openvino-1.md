This tutorial is a walk through an end-to-end AI project creating a face detection and recognition application in **Kibernetika**. We will begin by selecting data sets creating a project and selecting models, setting up the infrastructure, training those models, and completing by re-training for future proofing. 

Before we begin, let’s first address that there are two main steps to this project - face detection and face recognition. First, to detect that A face actually exists in the image and, second, to then recognize a specific face. Face detection includes Pnet, Rnet, and ONet neural nets to define face boundary boxes on a picture.

![](../img/tutorials/openvino/openvino1.png)

![](../img/tutorials/openvino/openvino2.png)

Face recognition includes calculating face embeddings using Inception ResNet model and training SVM classifier.

![](../img/tutorials/openvino/openvino3.png)

![](../img/tutorials/openvino/openvino4.png)

### Prepare DataSet for training

Start by creating a new dataset. In Kibernetika platform, we can do this using Web UI, CLI client or provided API. We will use Web UI.

* Open our demo dataset https://cloud.kuberlab.io/openvino-demo/catalog/dataset/open-faces/versions/1.0.0
* And **FORK** this dataset to one of your workspace

![](../img/tutorials/openvino-face/dataset1.gif)


### Create Project

Once we have this data set, we can go ahead and create a project. 

* Open pre defined project template https://cloud.kuberlab.io/kuberlab-demo/catalog/chart-mlapp-v2/openvino-facenet/readme/
* And install it to your workspace

> __ATTENTION: You MUST switch dataset during installation to your personal datasets that we created on the previous step!!! It is very important this project want work with datasets form other workspaces!!!__

![](../img/tutorials/openvino-face/create1.gif)

The project is now available to use.

### Convert Tensorflow model to OpenVino format

> NOTES: you can skip this step because our facenet model from catalog already has model in OpenVino format too.

To Convert project to OpenVino format we are going to execute our first task __model-converter__

![](../img/tutorials/openvino-face/convert1.gif)


Once model is converted the new model files now existing in the your personal model catalog.

![](../img/tutorials/openvino-face/convert2.gif)


From here, we will switch over to use the generated openvino model. 

* Open __SOURCES__ of your project and switch __facenet__ source to new created model

>__NOTES:__ make sure that you choose new created model from your current workspace.


### Build face recognition model

This brings us to the next part of the project, when we can actually start to train the face recognition model. This includes 3 sub tasks that we cluster together into pipeline task - Align images, train SVM model, and validate results.

>__NOTES:__ Use __pipeline__ task to build model. This task will automatically start align,train and validate tasks. Otherwise you need adjust parameter of each task, default parameters suitable only for whole piplene. 

![](../img/tutorials/openvino/openvino20.png)

Align performs cropping and will create a new version of the dataset that contains only cropped images.

![](../img/tutorials/openvino/openvino21.png)

The next task is to train SVM classifier using  Inception ResNet and openvino inference engine.

![](../img/tutorials/openvino/openvino22.png)

And the last task is validating the result and uploading the new model to model catalog. At this time, we generate a confusion matrix (confusion matrix keras) after the model validation to understand how accurate our new model is. 

![](../img/tutorials/openvino/openvino23.png)

### Start Serving

After the model is built, we can start the inference portion of this project. 

* Open __JOBS__ tab of your project
* Choose last __pipeline__ finished task and press start ___serv___ from context menu
* Leave all parameters as is
* Press start __SERV__

![](../img/tutorials/openvino-face/serv1.gif)

Now you can simple test your model

![](../img/tutorials/openvino-face/serv2.gif)

### Start serving from model catalog

Also new __facenet-classifier__ model will be pushed to __Model__ catalog after our __pipeline__ is done and validation was succeeded with accuracy more than 0.9.

You can start serving directly from __Model__ catalog.

* Choose new created __facenet-classifier__ model in the your __Model__ catalog
* From context menu chose edit and fill required serving parameters:
    * You could press __USE TEMPLATE__ button and choose __OpenVino Serving__ to fill some common parameters for  __OpenVino Serving__ backend
    * Execution command: kuberlab-serving --driver openvino --model-path $FACENET_DIR/facenet.xml --hooks serving_hook.py -o classifier=$MODEL_DIR/classifier.pkl -o flexible_batch_size=True -o resolutions=14x19,19x27,26x37,37x52,52x74,73x104,103x146,145x206,205x290 -o use_tf=true -o tf_path=$FACENET_DIR
    * Execution directory: $SRC_DIR
    * Resources:
        * CPU Requests: 100m
        * Memory Requests: 64Mi
        * CPU Max: 4
        * Memory Max: 4Gi
        * Replicas: 1
    * CPU image: kuberlab/serving:latest-openvino
    * Ports: name: grps, protocol: TCP, port: 9000, target port: 9000
    * Following volume required:
        * Source code for pre processing and post processing hook:
            * Name: src
            * SubPath: facenet/src
            * Type: GIT
            * Repository: https://github.com/kibernetika-ai/facenet
        * Model for face detection and inception open-vino model:
            * Name: facenet
	        * Type: Model
            * Model: __facenet-pretrained [kuberlab-demo]__ Or __facenet__ model from your catalog that was created after model converting task
            * Version: 2.0.0 or your version that should looks like __1.x.x-openvino-CPU-xxx__
    * Serving parameters. Required only for testing using Kibernetika UI.
	    * Out filter: output
        * Model: any
        * Out mime type: image/png
        * Raw Input: Yes
        * Params:
            * name: input, type: bytes

* Choose version that you want to serve and press __SERVE__ verify that all required parameter is filled as on previous step (sometimes it may require refresh page).
>NOTES: by default one additional volume __model__ will be added automatically to your serving configuration that will be refer to current(selected) version of model. Don't remove it.


### Retrain Model
Since data is likely to change over time in the real world, we can easily extend out the original dataset and continuously retrain the model. We call this Continuous Production and is a core funcion of the Kibernetika platform. Simply set up a new version, 1.0.1, add another person, Alex, and some images for that person. Reopen the project, switch the dataset to the new version and rebuild the model.

![](../img/tutorials/openvino/openvino30.png)

Again, once re-training and validation completed, you can see the model accuracy and then make informed decisions about deploying the new model to production. 

And, as a collaborative platform, you can easily share results, models, data, etc. with team members for a seamless rollout.

For more information on how you can accelerate your AI project with **Kibernetika**, reach us at info@kibernetika.ai today! 

