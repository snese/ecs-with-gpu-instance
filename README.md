# AWS ECS with GPU Instances

## AMI for GPU on ECS

You can reference the AWS official document, "[Creating a GPU Workload AMI](https://docs.aws.amazon.com/batch/latest/userguide/batch-gpu-ami.html)", install [nvidia-docker](https://github.com/NVIDIA/nvidia-docker), the containing driver for GPU on AMI and create AMI.

The nvidia-docker is a tool implemented as a docker wrapper, so that if you have NVIDIA drivers installed on the host OS, you can use the GPU from a container contain [CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit).

Referece: https://www.nvidia.com/object/docker-container.html

## Create an ECS cluster

Follow the document "[Creating a Cluster](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/create_cluster.html)", you can create a ECS Cluster and basically it's ok to create it with all default value.

## Register AMI in the CloudFormation behind the ECS cluster

## Create a TaskDifinition for GPU
