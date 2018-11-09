# PACE @GT : Setup ML/DL/RL libraries
-------------------------------------

## pytorch-0.4 with GPU capability [Python 2.7, Anaconda2]
----------------------------------------------------------

**Packages** : Gym, pytorch 

### Creating through environment file

Note: Try on compute node (rather than login node)

```bash
module load cuda/8.0.44
module load cudnn/7.5
module load anaconda2/latest
conda env create —name pytorch-test —file pytorch-gpu-env-test.yml
source activate pytorch-test
conda install pytorch==0.3.0 torchvision cuda80 -c pytorch
pip install pyglet==1.2.4
pip install http://download.pytorch.org/whl/cu80/torch-0.4.1-cp27-cp27mu-linux_x86_64.whl
conda install -c conda-forge glib [try twice if does not work once]
```

### Creating through scratch

```bash
module load cuda/8.0.44
module load cudnn/7.5
module load anaconda2/latest
conda create —clone tiny-20171117 —name rl
source activate rl
pip install opencv-python
pip install atari-py
conda install -c plotly plotly
pip install gym[atari]
conda install pytorch==0.3.0 torchvision cuda80 -c pytorch
pip install pyglet==1.2.4
pip install http://download.pytorch.org/whl/cu80/torch-0.4.1-cp27-cp27mu-linux_x86_64.whl
conda install -c conda-forge glib
```

### Testing pytorch installation
```python
import torch
print(torch.__version__)
torch.cuda.is_available()
torch.cuda.current_device()
torch.cuda.get_device_name(0)
```

## tensorflow-1.5.0 with GPU capability [Python 2.7, Anaconda2]
---------------------------------------------------------------

**Packages** : Gym, tensorflow

### Creating through environment file

```bash
module load cuda/8.0.44
module load cudnn/7.5
module load anaconda2/latest
conda env create —name tf-test —file env-tf-gpu-27.yml
```

### For Open-AI baselines 

```bash
source activate tf-test
git clone <my-openAI-baselines(2.7 py compatible)>
cd baselines
pip install -e .
export PYTHONPATH=~/.conda/envs/tf-test/lib/python2.7/site-packages:$PYTHONPATH
```

Troubleshoot:
pip install backports.tempfile

and provide correct path to backports.tempfile to PYTHONPATH variable (which is inside conda env)

Few checks:
  * `from backports import tempfile`


## References
----------------------------------------------------------
