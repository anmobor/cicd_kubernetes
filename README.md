# cicd_kubernetes

## Explanation of the system and components

The request to the services go inside the system through the Api Gateway and communicates to the service Mesh, and the service Mesh to the Kubernetes Pods with the microservices running inside. The Mesh controls the communication and interaction between pods and internal services.

When there is a change in the code in the code repository, the devops system throws the runners that compile and produce a docker container with the new features, this new version is stored in the AWS docker images registry, in the last stage of the CI/CD a new kubernetes pod is raised with new image replacing the old one and put into service.


## Components

### Api Gateway
Expose external API and services outwards, route the external traffic to the internal resources, in this case to the Mesh.

### Mesh 
It is in charge to direct towards services. Manages and handles the communication between the internal services inside the local network, offering network details.

### Kubernetes Pods
They hold the microservices with its API, and communicates and interacts through the Mesh with other pods and with the database.

### AWS Route 53
Stores all the DNS and IPs of the system, all connections are here defined.

### Code repository
Contains all the code of the microservices and the pipelines of the CI/CD.

### EC2 Runners
EC2 machine with the process to execute the pipelines of the CI/CD, it needs to have install all the technologies that the pipelines use.

### AWS Docker Images Registry
Stores all the docker images used by the pods. The pipelines run by the runners store here the images.

### AWS S3
Bucket with files used by system (files, documents, static web pages...) 
