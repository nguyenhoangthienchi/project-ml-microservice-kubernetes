[![CircleCI](https://dl.circleci.com/status-badge/img/gh/nguyenhoangthienchi/project-ml-microservice-kubernetes/tree/master.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/nguyenhoangthienchi/project-ml-microservice-kubernetes/tree/master)

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API.

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

Your project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:

- Test your project code using linting
- Complete a Dockerfile to containerize this application
- Deploy your containerized application using Docker and make a prediction
- Improve the log statements in the source code for this application
- Configure Kubernetes and create a Kubernetes cluster
- Deploy a container using Kubernetes and make a prediction
- Upload a complete Github repo with CircleCI to indicate that your code has been tested

---

## Set up the Environment

- Install Python3.7

```bash
sudo apt install libssl-dev libncurses5-dev libsqlite3-dev libreadline-dev libtk8.6 libgdm-dev libdb4o-cil-dev libpcap-dev
cd ~
wget https://www.python.org/ftp/python/3.7.3/Python-3.7.3.tar.xz
tar xvf Python-3.7.3.tar.xz
cd Python-3.7.3
./configure
sudo make
# Regularly common way is make install
# sudo make install
# Or using make altinstall to avoid override the existing Python lower version
sudo make altinstall
```

- Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv.

```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host.
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m virtualenv --python=<path-to-Python3.7> .devops
source .devops/bin/activate
```

- Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone: `python app.py`
2. Run in Docker: `./run_docker.sh`
3. Run in Kubernetes: `./run_kubernetes.sh`

### Kubernetes Steps

- Setup and Configure Docker locally
  - Install docker on official home page.
  - Verify through `docker -v`
- Setup and Configure Kubernetes locally
  - On Windows the best way is using Docker Desktop. Go into the setting -> Kubernetes -> Check on Enable Kubernetes.
  - Verify through `kubectl version --short`
- Create Flask app in Container
  - Run `./run_docker.sh`
- Run via kubectl
  - Run `./run_kubernetes.sh`

### Description of the files

- app.py: The API that use for predicting house pricing
- Dockerfile: The instruction for the docker build to build an image
- make_prediction.sh: The script to call API
- Makefile: The instruction file to set up environment, install dependencies, test and lint
- README.md: This file is containing help content.
- requirements.txt: Contains all dependencies.
- run_docker.sh: The script for running all steps with Docker.
- run_kubernetes.sh: Same as above but for Kubernetes.
- upload_docker.sh: The script for uploading an image into dockerhub for the kubernetes running.
- output_txt_files: Contain log of system.
- screenshots: inclues images
