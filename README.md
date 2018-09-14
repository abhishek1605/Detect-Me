# Detect-Me
Detect-Me is a Real-Time Object Detection Project using **Tensorflow Object Detection API** and **OpenCV**.

![1_q1uvc-mu-tc-wwfp2yxjow](https://user-images.githubusercontent.com/37084898/45520936-611ee100-b7d9-11e8-816b-38a4ff6cb3f4.gif)

## Project Description

The  Tensorflow Object Detection API is an open source framework built on tensorflow making it easy to construct, train and deploy object detection models.OpenCV is an open source computer vision library for image processing, machine learning and real-time detection. The API will be used to detect objects and OpenCV will be used to feed Real-Time Footage through webcam.

 **NOTE**: In my case I'll be using my laptop's Webcam. External webcams can also be used for better quality and frame rates.

## COCO DATASET 

The API has been trained on Microsoft COCO dataset { A dataset of about 300,000 images of 90 commonly found objects} with different trainable detection models. Below is the list of models that are pre-trained on COCO dataset.

![screenshot from 2018-09-14 00-21-17](https://user-images.githubusercontent.com/37084898/45521375-4baab680-b7db-11e8-8cdc-62b6a9979f5b.png)


**The higher the mAp (minimum average precision), the better the model.**

#### For my Project I'll be using  'ssdlite_mobilenet_v2_coco'(It is fast but has least accuracy).

**NOTE**:For Better accuracy models like 'faster_rcnn_inception_v2' or 'faster_rcnn_resent' can be used they have relatively more accuracy but requires heavier GPU for processing with slower speed as compared to 'ssdlite_mobilenet_v2'.  




## How to use ?

The above code can be used for **Real-Time Object Detection**. For this project I used Ubuntu 18.04 as my Primary Operating System and Python3.6 as My Primary Coding Language.

### Steps to follow: 

1.**Installing Dependencies**

Tensorflow Object Detection API depends on the following libraries:

*   Protobuf 3.0.0
*   Python-tk
*   Pillow 1.0
*   lxml
*   tf Slim (which is included in the "tensorflow/models/research/" checkout)
*   Jupyter notebook
*   Matplotlib
*   Tensorflow (>=1.9.0)
*   Cython
*   contextlib2
*   cocoapi

For detailed steps to install Tensorflow, follow the [Tensorflow installation
instructions](https://www.tensorflow.org/install/). A typical user can install
Tensorflow using one of the following commands:

``` bash
# For CPU
pip3 install tensorflow
# For GPU
pip3 install tensorflow-gpu
```

The remaining libraries can be installed on Ubuntu 16.04 using via apt-get:

``` bash
sudo apt-get install protobuf-compiler python3-pil python3-lxml python3-tk
pip3 install --user Cython
pip3 install --user contextlib2
pip3 install --user jupyter
pip3 install --user matplotlib
```

Alternatively, users can install dependencies using pip:

``` bash
pip3 install --user Cython
pip3 install --user contextlib2
pip3 install --user pillow
pip3 install --user lxml
pip3 install --user jupyter
pip3 install --user matplotlib
```

<!-- common_typos_disable -->
**Note**: sometimes "sudo apt-get install protobuf-compiler" will install
Protobuf 3+ versions for you and some users have issues when using 3.5.
If that is your case, try the [manual](#Manual-protobuf-compiler-installation-and-usage) installation.

2.**COCO API installation**

Download the
[cocoapi](https://github.com/cocodataset/cocoapi) and
copy the pycocotools subfolder to the tensorflow/models/research directory if
you are interested in using COCO evaluation metrics. The default metrics are
based on those used in Pascal VOC evaluation. To use the COCO object detection
metrics add `metrics_set: "coco_detection_metrics"` to the `eval_config` message
in the config file. To use the COCO instance segmentation metrics add
`metrics_set: "coco_mask_metrics"` to the `eval_config` message in the config
file.

```bash
git clone https://github.com/cocodataset/cocoapi.git
cd cocoapi/PythonAPI
make
cp -r pycocotools <path_to_tensorflow>/models/research/
```

3.**Protobuf Compilation**

The Tensorflow Object Detection API uses Protobufs to configure model and
training parameters. Before the framework can be used, the Protobuf libraries
must be compiled. This should be done by running the following command from
the tensorflow/models/research/ directory:


``` bash
# From tensorflow/models/research/
protoc object_detection/protos/*.proto --python_out=.
```

**Note**: If you're getting errors while compiling, you might be using an incompatible protobuf compiler. If that's the case, use the following manual installation

**Manual protobuf-compiler installation and usage**
Download and install the 3.0 release of protoc, then unzip the file.

```bash
# From tensorflow/models/research/
wget -O protobuf.zip https://github.com/google/protobuf/releases/download/v3.0.0/protoc-3.0.0-linux-x86_64.zip
unzip protobuf.zip
```

Run the compilation process again, but use the downloaded version of protoc

```bash
# From tensorflow/models/research/
./bin/protoc object_detection/protos/*.proto --python_out=.
```

4. **Add Libraries to PYTHONPATH**

When running locally, the tensorflow/models/research/ and slim directories
should be appended to PYTHONPATH. This can be done by running the following from
tensorflow/models/research/:


``` bash
# From tensorflow/models/research/
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
```

Note: This command needs to run from every new terminal you start. If you wish
to avoid running this manually, you can add it as a new line to the end of your
~/.bashrc file, replacing \`pwd\` with the absolute path of
tensorflow/models/research on your system.
 
 5. **Replacing Object_Detection Folder**
 
 Clone or download my repository. From tensorflow/models/research/ replace the Object_Detection folder with the existing folder.
 
 ```bash
 https://github.com/abhishek1605/Detect-Me.git
```
6. **Run the file**

Run the file named 'object_detection.py' in the pasted folder using the following command in the terminal:

``` bash
# From tensorflow/models/research/object_detection
python3 object_detection.py
```

## RESULTS: 

Here are some results.

![ezgif com-gif-maker](https://user-images.githubusercontent.com/37084898/45521839-84e42600-b7dd-11e8-9e9a-9ba7866c2893.gif)
![2hvr6h](https://user-images.githubusercontent.com/37084898/45521840-84e42600-b7dd-11e8-9d3d-94386abacf68.gif)

Please dont mind the quality of my webcam 😊, its an old one. I wish i could just **pip3 install upgrade**

 
 ## Contribute

If you want to contribute and add new feature feel free to send Pull request [here](https://github.com/abhishek1605/Detect-Me/pulls) :D

To report any bugs or request new features, head over to the [Issues page](https://github.com/abhishek1605/Detect-Me/issues)


## To-do

- [ ] Using the pre-trained model was really cool but I would love to train the API on my own dataset for super applications.
 
