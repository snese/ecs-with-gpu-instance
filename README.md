# AWS ECS with GPU Instance

## Environment

### Base AMI
[Deep Learning Base AMI (Amazon Linux)](https://aws.amazon.com/marketplace/pp/B077GFM7L7?qid=1543978509461&sr=0-6&ref_=srh_res_product_title)

Deep Learning AMI comes with CUDA 9 environment configured by default, but can be easily switched to CUDA 8: https://docs.aws.amazon.com/dlami/latest/devguide/tutorial-base.html

## AMI for GPU on ECS

We'll prebuild the nvidia docker 2 into the base AMI.

Reference the document, "[Creating a GPU Workload AMI](https://docs.aws.amazon.com/batch/latest/userguide/batch-gpu-ami.html)", install [nvidia-docker](https://github.com/NVIDIA/nvidia-docker), the containing driver for GPU on AMI and create AMI.

The nvidia-docker is a tool implemented as a docker wrapper, so that if you have NVIDIA drivers installed on the host OS, you can use the GPU from a container contain [CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit).

More detail: https://www.nvidia.com/object/docker-container.html

## Create an ECS cluster

Follow the document "[Creating a Cluster](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/create_cluster.html)", you can create a ECS Cluster and basically it's ok to create it with all default value.

## Register AMI in the CloudFormation behind the ECS cluster

ECS actually create the CloudFormation template behind the scenes. In order to change the type of instance started in the cluster and the underlying AMI you need to modify the CloudFormation template.

On the AWS CloudFormation console select **EC2ContainerService - ${cluster name}** (my cluster name is **ECS-GPU-Cluster**) and **Update Stack**.

![img1]


In **Specify stack details** update the **EcsAmiId** and **EcsInstanceType**

![img2]

## Create a TaskDifinition for GPU
