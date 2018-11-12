[![docker pulls](https://img.shields.io/docker/pulls/geezlab/cuda-tensorflow-pytorch-notebook.svg)](https://hub.docker.com/r/geezlab/cuda-tensorflow-pytorch-notebook/) [![docker stars](https://img.shields.io/docker/stars/geezlab/cuda-tensorflow-pytorch-notebook.svg)](https://hub.docker.com/r/geezlab/cuda-tensorflow-pytorch-notebook/) [![image metadata](https://images.microbadger.com/badges/image/geezlab/cuda-tensorflow-pytorch-notebook.svg)](https://microbadger.com/images/geezlab/cuda-tensorflow-pytorch-notebook "geezlab/cuda-tensorflow-pytorch-notebook image metadata")

# Docker Containers for Deep Learning 

> One-box depoyment of `TensorFlow, Keras, PyTorch, Jupyter Notebook, Lab, Hub, and NLP & ML stack`, with and without GPU support.


## Content

- Nvidia CUDA 9.0
- TensorFlow 1.11
- PyTorch 0.4.1
- Keras 2.2
- NLP Toolkits (`spaCy, nltk, torchtext`)
- Jupyter `Notebook, Lab, and Hub`
- Various machine learning libraries


## Usage

The following command pulls the latest image cuda-tensorflow-pytorch-notebook from Docker Hub if it is not already present on the local host. 

```
$ docker pull geezlab/cuda-tensorflow-pytorch-notebook:latest
```

Then start an ephemeral container named `dl-app` running a Jupyter Notebook server and exposes the server on host port `10000`. The command mounts the current working directory on the host as `/home/geez/dev` in the container. 

```
$ docker run --rm -p 10000:8888 -e JUPYTER_ENABLE_LAB=yes --runtime="nvidia" -v "$PWD":/home/geez/dev --name dl-app geezlab/cuda-tensorflow-pytorch-notebook:latest
```

The server logs appear in the terminal. Visiting `http://<hostname>:10000/?token=<token>` in a browser loads JupyterLab, where hostname is the name of the computer running docker and token is the secret token printed in the console. 

To check if GPU access has been enabled properly, open Terminal within Jupyter and run the following command. You should see details of the installed GPU device.

```
$ nvidia-smi
```

Docker destroys the container after notebook server exit, but any files written to ~/dev in the container remain intact on the host.  


## External Sources

This work heavily depends on the following resources:

- [Jupyter Docker-Stacks](https://github.com/jupyter/docker-stacks/)
- [Nvidia Cuda Docker](https://gitlab.com/nvidia/cuda/)

