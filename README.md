

## Overview
This repository contains  automation and infrastructure as code (IaC) projects. It is organized into multiple directories, each focusing on different aspects of automation and infrastructure setup.
Problem 1:
Gather information about all of the instances in
the current region. It should group them by the AMI’s that are in use, with information
about the AMI's and how many EC2 Instances are using them. Format the output as a
JSON object as below.
● Assume that AWS Credentials are available in the environment.
● If AMI’s are no longer available, null is an acceptable value for AMI
specific items. Do not assume that all AMI’s are owned by t
current account.
● Assume the environment being queried is a large account with lots of
instances and AMIs. Output results to stdout.

-Solution to Problem 1 of the Prompt is stored under directory 1_Automation


Problem 2:
Using Infrastructure-as-Code tool of choice, e.g., Terraform, Cloudformation, etc. to
provision the following set of resources in a given AWS account. Make sure you use
best practices, Nested Stacks in Cloudformation, or Modules in Terraform. Note that
in the given setup, incoming traffic on port 22 and port 443 goes to a Bastion ho
and an ELB, respectively to be forwarded to the web app server. The outgoing traff
from the web app server goes to a NAT to be sent to the Internet. Feel free to state
any assumptions implemented against


-Solution to Problem 2 of the Prompt is stored under directory 2_IaC
## Directory Structure

### 1_Automation

```mermaid
graph TD

    A[Python Script] --> B[Fetch EC2 Instances]
    A --> C[Group by AMI IDs]
    D[Bash Script] --> E[Use AWS CLI]
    D --> F[Format with jq]

```
- **For_Large_Infra**: Contains a Python script for gathering information about all EC2 instances in an AWS account, grouped by the AMI IDs they are using. This script is efficient, concise, and secure, offering a practical solution for AWS administrators and engineers who need to audit or manage EC2 resources effectively. [More details](1_Automation/For_Large_Infra/README.md)
    - **Why Python?**: Python was chosen for its readability and extensive libraries. The `boto3` library is used to interact with AWS services, making it easy to retrieve and manipulate AWS resources.
    - **AWS CLI**: Used for secure credential management and minimal exposure of sensitive AWS data.
    - **JSON Output**: The script outputs data in JSON format, which is easy to read and use for further processing.
    - **Error Handling**: Gracefully handles deregistered or unavailable AMIs by returning `null` for missing information.

- **Simpler_Bash_solution**: Contains a Bash script for retrieving information about all EC2 instances in an AWS account, grouped by the AMI IDs they are using. This script is efficient, concise, and secure, making it a practical tool for AWS administrators, DevOps professionals, and engineers who need to audit or manage EC2 resources effectively. [More details](1_Automation/Simpler_Bash_solution/README.md)
    - **Why Bash?**: Bash was chosen for its simplicity and ease of use in scripting. It is ideal for quick automation tasks and is widely used in DevOps.
    - **AWS CLI**: Used to retrieve information about EC2 instances and AMIs. Ensures secure credential management.
    - **jq**: A lightweight and powerful JSON parser used to handle and format JSON data in the script.
    - **JSON Output**: The results are output as a JSON file, making it easy to parse and use in other tools or reports.

### 2_IaC

- **terraform**: Demonstrates the provisioning of a secure, scalable, and highly available infrastructure on AWS using Terraform. It adheres to industry best practices, showcases modular design principles, and includes components such as VPC, bastion host, ELB, web servers, RDS (MySQL), and NAT Gateway. [More details](2_IaC/terraform/README.md)
    - **Why Terraform?**: Terraform was chosen for its ability to define and provision infrastructure as code. It ensures consistency and repeatability in deploying AWS resources.
    - **Modular Design**: The project is structured with reusable components for scalability and clarity. This modular approach allows for independent modification of individual components without impacting the entire infrastructure.
    - **Security Best Practices**: Includes state file management, secrets management, IAM policies, security groups, encryption, and monitoring and logging to ensure a secure and robust infrastructure.
    - **Deployment Steps**: Detailed steps for cloning the repository, initializing Terraform, customizing variables, validating configuration, planning and applying the deployment, accessing outputs, and destroying resources.

```mermaid
graph TD

    A[Initialize Terraform] --> B[Validate Configuration]
    B --> C[Plan Infrastructure]
    C --> D[Apply Configuration]
    D --> E[Provision Resources]
```

## Contact
For any issues or questions, please reach out via email: aqilshaikh94@gmail.com
