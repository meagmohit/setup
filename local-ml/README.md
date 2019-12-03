# Local ML Stuff : Essential Commands
-------------------------------------


## Conda
--------

1. [Anaconda Cheat Sheet](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)


## Jupyter Notebook
-------------------

* `which jupyter` : tells the location of jupyter installation being used


## GPU stuff
------------

*  `nvcc --version` CUDA Version
*  `nvidia-smi` NVIDIA Management Interface: GPU information and usage
*  `export CUDA_VISIBLE_DEVICES=1` : Provide access to only GPU:0 device
*  `echo $CUDA_VISIBLE_DEVICES`: Check the value of this flag

## Tensorflow
-------------
*  `print(tf.__version__)` in python for tensorflow version
*  `tf.test.is_gpu_available()`: Check if GPU is available
*  `tf.test.gpu_device_name()`: Get the info of available GPU devices
