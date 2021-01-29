# Docker containers for deep learning and GPU-accelerated computing

### Overview
The containers are intended to run on a GPU-equipped machine, either a local computer or a remote server, e.g. a VM instance on AWS or GCP, etc..  
The repo includes 5 Dockerfiles. They are for uses of general Python for CUDA, cupy, Tensorflow, PyTorch and Julia, respectively, all built from various nvidia/cuda images as base images. Most components will be updated versions to take advantage of new developments.

### Usage
To use the Dockerfiles, one may need a GPU enabled machine, for example an AWS p2 instance, ideally running a deep learning AMI, or at least having drivers installed.
Clone the repository and build from any Dockerfile of choice:
```sh
docker build -f ./dockerfiles/Dockerfile.<ver> -t <image_tag> .
```
And run the image with GPU enabled:
```sh
docker run --gpus all --name <name> -d -p 28888:8888 -v "$(pwd)"/notebooks:/src/notebooks <image_tag>
```
Obviously, omit the `--gpus all` flag when GPU is absent, and change mount point accordingly.

### References
Including following Github repositories:  
[ageron/handson-ml2](https://github.com/ageron/handson-ml2)  
[pytorch/examples](https://github.com/pytorch/examples)  
[fastai/fastbook](https://github.com/fastai/fastbook)  
[tensorflow/examples](https://github.com/tensorflow/examples)  
[floydhub/tensorflow-examples](https://github.com/floydhub/tensorflow-examples)  
[JuliaAcademy/JuliaTutorials](https://github.com/JuliaAcademy/JuliaTutorials)  
[UCIDataScienceInitiative/IntroToJulia](https://github.com/UCIDataScienceInitiative/IntroToJulia)  

The install script for Julia is modified install section from the notebook: [Julia for pythonistas](https://colab.research.google.com/github/ageron/julia_notebooks/blob/master/Julia_for_Pythonistas.ipynb).


### Future work
- Add container for R/R Studio.
- Add guides for cupy.