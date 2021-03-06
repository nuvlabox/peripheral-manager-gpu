# peripheral-manager-gpu

# peripheral-manager-gpu


[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg?style=for-the-badge)](https://github.com/nuvlabox/peripheral-manager-gpu/graphs/commit-activity)


[![CI](https://img.shields.io/travis/com/nuvlabox/peripheral-manager-gpu?style=for-the-badge&logo=travis-ci&logoColor=white)](https://travis-ci.com/nuvlabox/peripheral-manager-gpu)
[![GitHub issues](https://img.shields.io/github/issues/nuvlabox/peripheral-manager-gpu?style=for-the-badge&logo=github&logoColor=white)](https://GitHub.com/nuvlabox/peripheral-manager-gpu/issues/)
[![Docker pulls](https://img.shields.io/docker/pulls/nuvlabox/peripheral-manager-gpu?style=for-the-badge&logo=Docker&logoColor=white)](https://cloud.docker.com/u/nuvlabox/repository/docker/nuvlabox/peripheral-manager-gpu)
[![Docker image size](https://img.shields.io/microbadger/image-size/nuvlabox/peripheral-manager-gpu?style=for-the-badge&logo=docker&logoColor=white)](https://cloud.docker.com/u/nuvlabox/repository/docker/nuvlabox/peripheral-manager-gpu)

![logo](https://camo.githubusercontent.com/5f893cf6632a9d635c0bdb1c0b51fc97317ce498/68747470733a2f2f6d656469612e73697873712e636f6d2f68756266732f53697853715f47656e6572616c2f6e75766c61626f785f6c6f676f5f7265645f6f6e5f7472616e73706172656e745f3235303070782e706e67)


**This repository contains the source code for the NuvlaBox Peripheral Manager for GPU devices - this microservice is responsible for the discovery, categorization and management of all [NuvlaBox](https://sixsq.com/products-and-services/nuvlabox/overview) GPU peripherals.**

This microservice is an integral component of the NuvlaBox Engine.


---

**NOTE:** this microservice is part of a loosely coupled architecture, thus when deployed by itself, it might not provide all of its functionalities. Please refer to https://github.com/nuvlabox/deployment for a fully functional deployment

---

## Build the NuvlaBox Peripheral Manager for GPU devices

This repository is already linked with Travis CI, so with every commit, a new Docker image is released. 

There is a [POM file](pom.xml) which is responsible for handling the multi-architecture and stage-specific builds.

**If you're developing and testing locally in your own machine**, simply run `docker build .` or even deploy the microservice via the local [compose files](docker-compose.yml) to have your changes built into a new Docker image, and saved into your local filesystem.

**If you're developing in a non-master branch**, please push your changes to the respective branch, and wait for Travis CI to finish the automated build. You'll find your Docker image in the [nuvladev](https://hub.docker.com/u/nuvladev) organization in Docker hub, names as _nuvladev/peripheral-manager-gpu:\<branch\>_.

## Deploy the NuvlaBox Peripheral Manager for GPU devices

The NuvlaBox Peripheral Manager for GPU will only work if a [Nuvla](https://github.com/nuvla/deployment) endpoint is provided and a NuvlaBox has been added in Nuvla.

Why? Because this microservice has been built to report directly to Nuvla. Every GPU device will be registered in Nuvla and associated with **an existing** NuvlaBox.

### Prerequisites 

 - *Docker (version 18 or higher)*
 - *Docker Compose (version 1.23.2 or higher)*
 - *Linux*

### Environment variables

|                          	|                                                                                                                                                       	|
|-------------------------	|------------------------------------------------------------------------------------------------------------------------------------------------------	|
|           NUVLABOX_UUID 	| (**required**) before starting the microservice, make sure you export the ID of the NuvlaBox you've created through Nuvla: `export NUVLABOX_UUID=<nuvlabox id from nuvla>` 	|
| NUVLA_ENDPOINT_INSECURE 	| if you're using an insecure Nuvla endpoint, set this to `True`: `export NUVLA_ENDPOINT_INSECURE=True`                                                	|
|          NUVLA_ENDPOINT 	| if you're not using [nuvla.io](https://nuvla.io) then set this to your Nuvla endpoint: `export NUVLA_ENDPOINT=<your endpoint>`                                      	|
| | |

### Launching the NuvlaBox Peripheral Manager for GPU devices

Simply run `docker-compose up --build`

### If Nuvla is running on `localhost`

Simply run `docker-compose -f docker-compose.localhost.yml up --build`

## Testing 

This microservice is completely automated, meaning that as long as all the proper environment variables have been correctly set and the right dependencies have been met, the respective Docker container will start by itself and automatically start registering peripherals into Nuvla, in real-time.

## Contributing

This is an open-source project, so all community contributions are more than welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md)
 
## Copyright

Copyright &copy; 2019, SixSq Sàrl