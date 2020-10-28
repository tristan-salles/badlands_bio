# badlands_bio

Collection of Jupyter notebooks to run landscape elevation models with a biodiversity flavour!

## Software

The notebooks rely on two main scientific software:

1.  [badlands](https://badlands.readthedocs.io/en/latest/) provided within the docker container below,
2. [circuitscape](https://circuitscape.org) that will need to be downloaded in addition to the container


## Container

In addition, several libraries and scripts are required and have been packaged in a Docker container. So on top of the notebooks available in this repository it is recommended to download the following container:

+ [geodels/gospl:bio](https://hub.docker.com/layers/geodels/gospl/bio/images/sha256-98901c380d2ffd3b6b3f2f76f5df07c71fd4f90c9661ab2e33036cbd179331ef?context=repo)

### Pulling the image

Once you have installed Docker on your system, you can pull the image as follow:

`docker pull geodels/gospl:bio`

You can list all the images available on your system as follow:

`docker images`

An image can be deleted as follow:

`docker rmi geodels/gospl`

### Starting the container from a terminal

You can then start a docker container (an instance of an image):

`docker run -d --name my_container -p 8888:8888 -v my_vol:/live/share geodels/gospl:bio`
   
You can access the container via your browser at the following address: http://localhost:8888

It is also possible to `ssh` into the container as follow:

`docker run -it -v my_vol:/live/share  --entrypoint /bin/bash geodels/gospl:bio`

You can list the containers currently existing on your machine by running:

`docker ps -a`

The `-a` means “all container”. The docker `ps` command only list running containers.

Docker containers can be stop (so that they do not use CPU or RAM resource):

`docker stop my_container`

They can also be deleted:

`docker rm my_container`

> It’s a good idea to keep track of how many containers have been created as they can rapidly take a lot of space on your machine.

### Kitematic

Kitematic is a program that provides a graphical user interface to the docker daemon and to Docker Hub.

#### Downloading a tagged image

The software is available for Windows, Mac OS X and Linux. Be aware that on linux the installation may differ depending on the distribution you are running.

1. Download and Install Kitematic
2. Open Kitematic and search for the tag corresponding to a specific the gospl version.
3. Download the container by clicking on the create button.

#### Linking a local volume

You should now have a container appearing on the left side of your kitematic window.

The first thing to do now is to create a link between a local directory (A directory on your physical hard drive) and a volume directory inside the docker container. A volume is a special directory that can be accessed from outside the container. It is the location you will use to save your own results.

## Examples of dataset

+ **Precipitation grids**: download dataset from http://www.paleoclim.org and we use the variable Bio_12: Annual Precipitation [mm/year].
+ **Digital elevation grids**: download dataset from https://www.ngdc.noaa.gov/mgg/global/ using the ETOPO1 Bedrock geotiff for example.

