# CD

## Table of Contents
- [Description](#description)
- [Variables](#variables)
- [Jobs](#jobs)
- [Credentials](#credentials)
- [Test Runner](#runner)

### Description 
This workflow is triggered when a pull request is opened on the HyperBEAM main branch. It is responsible for installing and running the HyperBEAM rebar3 eunit tests.

### Variables

The following variables are defined by the workflow:

### Jobs

The workflow consists of 1 main job:

1. **test**: 


### Credentials

### Runner

This workflow uses a self hosted github test runner to create the github test runner follow the below steps - 

1. Create an Ubuntu 22.04 instance, shut down root login, create a sudo user, and login as the new user
2. In Settings -> Actions -> Runners on this repo, create a runner called self-hosted. Run these commands on it with the correct token for your runner

```
mkdir actions-runner && cd actions-runner

curl -o actions-runner-linux-x64-2.324.0.tar.gz -L https://github.com/actions/runner/releases/download/v2.324.0/actions-runner-linux-x64-2.324.0.tar.gz

echo "e8e24a3477da17040b4d6fa6d34c6ecb9a2879e800aa532518ec21e49e21d7b4  actions-runner-linux-x64-2.324.0.tar.gz" | shasum -a 256 -c

tar xzf ./actions-runner-linux-x64-2.324.0.tar.gz

./config.sh --url https://github.com/VinceJuliano/HyperBEAM --token <your runner token>

sudo ./svc.sh install

sudo ./svc.sh start
```