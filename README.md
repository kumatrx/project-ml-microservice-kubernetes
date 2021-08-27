[![CircleCI](https://circleci.com/gh/kumatrx/project-ml-microservice-kubernetes.svg?style=svg)](https://circleci.com/gh/kumatrx/project-ml-microservice-kubernetes)

# Operationalize a Machine Learning Microservice API

## Project Overview

In this project, a pre-trained, `sklearn` model is provided that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. Data is initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project operationalize a Python flask app—in a provided file, `app.py` —that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

Project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. The project includes:
* Make file to install all the dependencies provided in requirements.txt
* Testing - code ( linting ) - hadolint
* A Dockerfile to containerize this application
* Deployment of containerized application using Docker and making a prediction
* Improved log statements (output) in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deployment of a container using Kubernetes and make prediction
* A complete Github repo with CircleCI is uplaoded to indicate that code has been tested

## Setup the Environment

* Project files are provided on github link. Clone the files using below link in terminal.
`$ git clone https://github.com/kumatrx/project-ml-microservice-kubernetes.git`

Make sure to `$ cd project-ml-microservice-kubernetes` in terminal to access all files. 

* Create a virtualenv and activate it 
`python3 -m venv ~/.devops`
`source ~/.devops/bin/activate`
* Run `make install` to install the necessary dependencies

* install Hadolint using following command:
`sudo wget -O /bin/hadolint https://github.com/hadolint/hadolint/releases/download/v1.16.3/hadolint-Linux-x86_64`
`sudo chmod +x /bin/hadolint`

* install Hadolint using following command:
`sudo wget -O /bin/hadolint https://github.com/hadolint/hadolint/releases/download/v1.16.3/hadolint-Linux-x86_64`
`sudo chmod +x /bin/hadolint`

* install Minikube using following command:
`curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64`
`sudo install minikube-linux-amd64 /bin/minikube`
`sudo chmod +x /bin/minikube`

* install Kubectl using following command:
`curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"`
`sudo install kubectl /bin/kubectl`
`sudo chmod +x /bin/kubectl`

### Running `app.py`

Script files are provided with the code with the extension '.sh'. 

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
    * While the server is listening on Port= 8000, open another terminal and in the same folder run file
        `./make_prediction.sh`
    * A prediction can be seen in terminal in case of succesfull execuation.
    * In the listening terminal, you can see a status 200 -.
3. Run in Kubernetes:  `./run_kubernetes.sh`
    * In terminal you can see an IP address and port number. Copy that address and edit make_prediction_2.sh file with the correct port and address in line 3 and 28.
    * open another terminal and in the same folder run file
        `./make_prediction.sh`
    * In the listening terminal, you can see a successfull prediction
4. There is a folder named '.circleci' that includes a config.yml file. In case if you have plan to push the repo to github. Just add the repo in circleci account and look at the final tests if they pass or fail. 
5. You can see a badge in the top in README file that show `PASSED` in green color to confirm the successfull execution.

### Kubernetes Steps
* Setup and Configure Docker locally
   * Install docker and create docker hub account
* Setup and Configure Kubernetes locally
   * Install a virtual machine like VirtualBox and minikube
   * Start a local cluster: minikube start
* Create Flask app in Container
   * Build image and add a descriptive tag: docker build --tag=app .
   * Upload docker image: ./upload_docker.sh where your docker id should be used
* Run via kubectl
   * Run in Kubernetes: ./run_kubernetes.sh where dockerpath should be same name as defined above
   * Make prediction using second terminal: make_prediction.sh

## Author

* Tarun Kumar <br />
  __ _Data Engineer_ <br />
