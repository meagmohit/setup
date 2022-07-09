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

## Installing CUDA on Alienware R10 w/ RTX 3060
-----------------------------------------------
* Issues with pytorch/GPU: https://discuss.pytorch.org/t/trouble-installing-torch-with-cuda-using-conda-on-wsl2/136911/2
* 

## Installing CUDA on Alienware R8
----------------------------------
* Before installing from NVIDIA's website, follow the pre-installation steps from https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#pre-installation-actions
* Choose the appropriate version from  https://developer.nvidia.com/cuda-downloads and follow the instructions given in the website.
* Follow the post-installation instructions from https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#post-installation-actions

## Installing CUDNN
-------------------
* Download and install the developer version from https://developer.nvidia.com/rdp/cudnn-download
* Follow the test steps from https://docs.nvidia.com/deeplearning/sdk/cudnn-install/index.html

## In case of CUDA malfunction
* If CUDA malfunctions and does not allow logging into Ubuntu, press `Ctrl + Alt + F2` and log in to the terminal. Use `sudo apt-get purge nvidia*` to remove all nvidia applications.
* Add `nomodeselect` in boot options by pressing `e` and running `sudo update-grub2` to save the bootloader settings till the issue is fixed.
* Boot normally back into Ubuntu GUI. GUI will be low resolution and laggy. Follow the instructions to install CUDA and CUDNN. 
* Change boot options using `sudo gedit /etc/default/grub` and remove `nomodeselect`. Run, `sudo update-grub2`.
* Reboot!
