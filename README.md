# Packer AMI Creation for AWS

This repository automates the creation of Amazon Machine Images (AMIs) using Packer. It contains all the necessary configurations and scripts for building a customized AMI that can be used for launching EC2 instances.

## File Structure

- **Jenkinsfile**: Jenkins pipeline configuration for automating the Packer build process.
- **README.md**: Documentation about the repository and its usage (this file).
- **aws.pkr.hcl**: Packer configuration file for defining the AWS provider, region, and AMI settings.
- **build.pkr.hcl**: Packer build file that contains the AMI building process and configuration.
- **locals.pkr.hcl**: Local variables used in the Packer configuration to define reusable values.
- **plugins.pkr.hcl**: Configuration for Packer plugins used during the build process.
- **provisioner.sh**: Shell script for configuring the AMI during the build process.
- **values_pkrvars.hcl**: File containing values for variables used during the build process (e.g., instance types, region).
- **variables.pkr.hcl**: File that defines the variables used across Packer configuration files.

## Requirements

- **Packer**: The HashiCorp tool used for building machine images.
- **AWS CLI**: Configured with necessary credentials for creating AMIs in AWS.
- **Jenkins**: For automating the build process (optional if not using Jenkins).
- **SSH Access**: Ensure that your AWS credentials have appropriate permissions to create AMIs, EC2 instances, etc.

## Usage

### 1. Clone the Repository

```bash
git clone <repository_url>
cd <repository_directory>

customize Variables
Edit the values_pkrvars.hcl file to customize the AMI creation, such as region, instance type, and any other preferences for your build.

hcl
Copy
region = "us-west-2"
ami_name = "custom-ami"
instance_type = "t2.micro"
Install Packer
Ensure that you have Packer installed. You can check the installation by running:
packer --version

export AWS_ACCESS_KEY_ID=<your-access-key-id>
export AWS_SECRET_ACCESS_KEY=<your-secret-access-key>

Build the AMI
Run Packer to build the AMI by executing:

bash
Copy
packer build -var-file=values_pkrvars.hcl build.pkr.hcl



