# Video to Events: Recycling Video Datasets for Event Cameras

<p align="center">
  <a href="https://youtu.be/uX6XknBGg0w">
    <img src="http://rpg.ifi.uzh.ch/data/VID2E/thumb.png" alt="Video to Events" width="600"/>
  </a>
</p>

This repository contains code that implements 
video to events conversion as described in Gehrig et al. CVPR'20. The paper can be found [here](http://rpg.ifi.uzh.ch/docs/CVPR20_Gehrig.pdf)

If you use this code in an academic context, please cite the following work:

[Daniel Gehrig](https://danielgehrig18.github.io/), Mathias Gehrig, Javier Hidalgo-Carrió, [Davide Scaramuzza](http://rpg.ifi.uzh.ch/people_scaramuzza.html), "Video to Events: Recycling Video Datasets for Event Cameras", The Conference on Computer Vision and Pattern Recognition (CVPR), 2020

```bibtex
@InProceedings{Gehrig_2020_CVPR,
  author = {Daniel Gehrig and Mathias Gehrig and Javier Hidalgo-Carri\'o and Davide Scaramuzza},
  title = {Video to Events: Recycling Video Datasets for Event Cameras},
  booktitle = {{IEEE} Conf. Comput. Vis. Pattern Recog. (CVPR)},
  month = {June},
  year = {2020}
}
```

## Basic setup

### Ready to use

SSH into one of the student workstations
```bash
ssh ethz-username@tardis-aNN.ee.ethz.ch
```
where `NN` is a number, e.g. 08. Then run
```bash
source /home/mirieder/.bashrc_miniconda3
conda activate vid2e
```
Then the Python environment is ready to use.

### Manual installation

Clone the repo *recursively with submodules*

```bash
git clone https://github.com/miried/rpg_vid2e.git --recursive
```

## Installation with [Anaconda](https://www.anaconda.com/distribution/)
_Note: The student workstations in the computer lab have a disk quota for your home directory of 5GB. The following works only on your own computer. If you are using the student workstations, see "Using /scratch/"_

Run the following commands

```bash
conda create -y -n vid2e
conda activate vid2e

conda install -y pytorch torchvision cudatoolkit opencv tqdm eigen boost boost-cpp pybind11 jupyterlab matplotlib
conda install -y -c conda-forge scikit-video
```


### Using /scratch/
If you get a disk quota error, then anaconda filled up your home directory. You can clear up some space with
```bash
conda remove --name vid2e --all
conda clean --all
```
and then make a new environment on `/scratch/`. `/scratch/` is a file system local on your workstation which does not have a quota. Create your own subdirectory with
```bash
mkdir /scratch/$USER
```
and then make the conda environment with
```bash
conda create --prefix /scratch/$USER/vid2e
```

### Installing ESIM

Build the python bindings for ESIM

```bash
cd esim_py
pip install .
```
Perfect! Now you can open the Jupyter notebook and convert your own video. You may also use the `drop.avi` example.

## Adaptive Upsampling
*This package provides code for adaptive upsampling with frame interpolation based on [Super-SloMo](https://people.cs.umass.edu/~hzjiang/projects/superslomo/)*

Consult the [README](upsampling/README.md) for detailed instructions and examples.

## esim\_py
*This package exposes python bindings for [ESIM](http://rpg.ifi.uzh.ch/docs/CORL18_Rebecq.pdf) which can be used within a training loop.*

For detailed instructions and example consult the [README](esim_py/README.md)
