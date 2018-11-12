[![docker pulls](https://img.shields.io/docker/pulls/geezlab/gpu-deep-learning-notebook.svg)](https://hub.docker.com/r/geezlab/gpu-deep-learning-notebook/) [![docker stars](https://img.shields.io/docker/stars/geezlab/gpu-deep-learning-notebook.svg)](https://hub.docker.com/r/geezlab/gpu-deep-learning-notebook/) [![image metadata](https://images.microbadger.com/badges/image/geezlab/gpu-deep-learning-notebook.svg)](https://microbadger.com/images/geezlab/gpu-deep-learning-notebook "geezlab/gpu-deep-learning-notebook image metadata") [![docker pulls](https://img.shields.io/docker/pulls/geezlab/cpu-deep-learning-notebook.svg)](https://hub.docker.com/r/geezlab/cpu-deep-learning-notebook/) [![docker stars](https://img.shields.io/docker/stars/geezlab/cpu-deep-learning-notebook.svg)](https://hub.docker.com/r/geezlab/cpu-deep-learning-notebook/) [![image metadata](https://images.microbadger.com/badges/image/geezlab/cpu-deep-learning-notebook.svg)](https://microbadger.com/images/geezlab/cpu-deep-learning-notebook "geezlab/cpu-deep-learning-notebook image metadata")

# [CPU/GPU] Docker Containers for Deep Learning

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

The following command pulls the latest image of` deep-learning-notebook` from Docker Hub, if it is not already present on the local host. 

> To use the `CPU` version replace `gpu` with `cpu` in all commands.

```
$ docker pull geezlab/gpu-deep-learning-notebook:latest
```

Then start an ephemeral container named `dl-app` running a Jupyter Notebook server and exposes the server on host port `10000`. The command mounts the current working directory on the host at `/home/geez/dev` in the container. 

```
$ docker run --rm -p 10000:8888 -e JUPYTER_ENABLE_LAB=yes --runtime="nvidia" -v "$PWD":/home/geez/dev --name dl-app geezlab/gpu-deep-learning-notebook:latest
```

The server logs appear in the terminal. Visiting `http://<hostname>:10000/?token=<token>` in a browser loads JupyterLab, where hostname is the name of the computer running docker and token is the secret token printed in the console. 

To check if GPU access has been enabled properly, open Terminal within Jupyter and run the following command:

```
$ nvidia-smi
```

Thaat should print details of the installed GPU device/s.

> Note that docker destroys the container after the notebook server exits, but all files written to `~/dev` directory in the container remain intact on the host.  


## External Sources

This work heavily depends on the following resources:

- [Jupyter Docker-Stacks](https://github.com/jupyter/docker-stacks/)
- [Nvidia Cuda Docker](https://gitlab.com/nvidia/cuda/)

