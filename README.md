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

* To install Hadolint use following command depending on the choice of OS:

    * For MAC: `brew install hadolint`
    * For Windows: `scoop install hadolint` (Need to install scoop before using this command)

Dockers, virtual box and minikube must be installed in order to run application. 

### Special Instructions For Windows 10 Pro Users:

Windows provide a hyperV setup instead of virtualbox. This hyperV supports linux subsystems and Docker VM. But to run minikube on hyperV must follow these steps:

1. Open hyper-V manager and click on Virtual Switch Manager (right menu)
2. Create new Virtual Network Switch (external) with a name `Primary Network Switch`.
3. Click on this newly created switch and select your wifi as external network.
4. Restart your computer and install minikube using following command:
    * `choco install minikube`
    * `choco install kubernetes-cli`
    * Finally run the command that will launch minikube on hyperV
        `minikube start --vm-driver hyperv --hyperv-virtual-switch "Primary Virtual Switch"`
5. In windows, a linux subsystem (ubuntu) can be installed from Microsoft Store.
6. In order to connect to docker for Windows, just enable "Expose daemon on tcp://localhost:2375 without TLS in docker settings".
7. Set enviroment variable in linux subsystem by executing this command in linux subsystem terminal
    `echo "export DOCKER_HOST=localhost:2375" >> ~/.bash_profile` (or a '.bashrc') file.
8. In order to test it run `docker images` to verify if it is configured properly.

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
        `./make_prediction_2.sh`
    * In the listening terminal, you can see a successfull prediction
4. There is a folder named '.circleci' that includes a config.yml file. In case if you have plan to push the repo to github. Just add the repo in circleci account and look at the final tests if they pass or fail. 
5. You can see a badge in the top in README file that show `PASSED` in green color to confirm the successfull execution.

## Author

* Tarun Kumar <br />
  __ _Data Engineer_ <br />
