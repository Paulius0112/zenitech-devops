# Zenitech DevOps internship project
In this project, we will be using Ansible to automate the deployment AWS S3 storage bucket and configure an already created E2 instance to serve static content from the S3 to the web.
## Task
- Create an AWS account
- Create an S# bucket
- Upload index.html with any content to S# bucket
- Create a public EC2 instance

## To start

### Launch E2 instance
Tutorial on how to launch AWS E2 instance can be found [here](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/step-1-launch-instance.html)

For this tutorial, the information of created E2 instance can be found below
| **Instance type** |  **vCPUs**  | **Memory (GiB)** | **Instance Storage (GB)** | **Network Performance** |
|:-----|:--------:|------:|------:|------:|
| t2.small   | 1 | 2 | EBS only | Low to Moderate |

 
### Ansible install on host machine
Tutorial on how to install Ansible can be found [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## Configuration
### Define host
For Ansible playbook to execute successfully, `inventory.ini` in `hosts` directory should modified. For demonstratino purposes, the information is provided of already create AWS E2 instance.

```[vm]
18.217.236.79 ansible_connection=ssh ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/aws-private.pem```

### Define variables
In the `vars` folder, `main.yml` file should be modified with required values. For demonstration purposes, the information is provided of an already created IAM user.
```AWS_ACCESS_KEY: AKIA3HTXCJQA5ALLRFOZ 
AWS_SECRET_KEY: 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
BUCKET_NAME: zenitech-paulgasp
AWS_REGION: eu-west-1```

## Run ansible playbook
The ansible playbook can be executed with the following command
`ansible-playbook -i hosts/inventory.ini main.yml -vvv -e 'ansible_python_interpreter=/usr/bin/python3`

## Congratulations! Your E2 instance is now taking an `index.html` and `error.html` files from created S3 bucket and serving a static content on the web. You can see that by visiting the [link]()
