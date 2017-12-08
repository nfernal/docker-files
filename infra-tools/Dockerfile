#
# nfernal Dockerfile
#
# https://github.com/dockerfile/nfernal
#

# Pull base image.
FROM centos:latest

# Update the image with the latest packages (recommended)
RUN yum install epel-release -y; yum clean all

RUN yum update -y; yum clean all

RUN yum install wget python-pip zip unzip -y; yum clean all

RUN curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip" && unzip awscli-bundle.zip && ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws

RUN rpm -ivh https://packages.chef.io/files/stable/chefdk/1.6.1/el/7/chefdk-1.6.1-1.el7.x86_64.rpm

RUN curl "https://releases.hashicorp.com/packer/1.1.2/packer_1.1.2_linux_amd64.zip" -o "packer_1.1.2_linux_amd64.zip" && unzip packer_1.1.2_linux_amd64.zip && mv packer /usr/local/bin && rm -f packer_1.1.2_linux_amd64.zip

RUN curl "https://releases.hashicorp.com/terraform/0.10.7/terraform_0.10.7_linux_amd64.zip" -o "terraform_0.10.7_linux_amd64.zip" && unzip terraform_0.10.7_linux_amd64.zip && mv terraform /usr/local/bin && rm -f terraform_0.10.7_linux_amd64.zip

RUN wget https://github.com/gruntwork-io/terragrunt/releases/download/v0.13.7/terragrunt_linux_amd64 && mv terragrunt_linux_amd64 terragrunt && mv terragrunt /usr/local/bin && chmod +x /usr/local/bin/terragrunt

# Define working directory.
WORKDIR /opt

# Define default command.
CMD ["bash"]
