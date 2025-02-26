# DevOps Cheat Sheet and Reference Guide

## Table of Contents

- [Git Commands](#git-commands)
- [Docker Commands](#docker-commands)
- [Kubernetes Commands](#kubernetes-commands)
- [CI/CD Concepts](#cicd-concepts)
- [Linux Commands](#linux-commands)
- [Bash Scripting Tips](#bash-scripting-tips)
- [Cloud CLI Commands](#cloud-cli-commands)
- [Monitoring & Observability](#monitoring--observability)
- [Security Best Practices](#security-best-practices)

## Git Commands

### Basic Commands

```bash
# Initialize a repository
git init

# Clone a repository
git clone <repository-url>

# Check status
git status

# Add files to staging
git add <filename>    # Add specific file
git add .             # Add all files

# Commit changes
git commit -m "Commit message"

# Push changes
git push origin <branch>

# Pull changes
git pull origin <branch>
```

### Branching

```bash
# Create and checkout a new branch
git checkout -b <branch-name>

# List all branches
git branch -a

# Switch to a branch
git checkout <branch-name>

# Merge a branch
git merge <branch-name>

# Delete a branch
git branch -d <branch-name>  # Local delete
git push origin --delete <branch-name>  # Remote delete
```

### Advanced Git

```bash
# Stash changes
git stash
git stash pop

# View commit history
git log
git log --oneline --graph --decorate

# Undo last commit but keep changes
git reset HEAD~1

# Undo last commit and discard changes
git reset --hard HEAD~1

# Amend last commit
git commit --amend -m "New commit message"

# Rebase
git rebase -i HEAD~3  # Interactive rebase for last 3 commits
```

## Docker Commands

### Containers

```bash
# Run a container
docker run <image-name>
docker run -d -p 8080:80 --name my-container <image-name>

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop/start containers
docker stop <container-id/name>
docker start <container-id/name>

# Remove container
docker rm <container-id/name>

# Execute command in running container
docker exec -it <container-id/name> /bin/bash

# View container logs
docker logs <container-id/name>
docker logs -f <container-id/name>  # Follow logs
```

### Images

```bash
# List images
docker images

# Build image from Dockerfile
docker build -t <image-name:tag> .

# Remove image
docker rmi <image-id/name>

# Push image to registry
docker push <image-name:tag>

# Pull image from registry
docker pull <image-name:tag>
```

### Docker Compose

```bash
# Start services
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs

# Build and recreate services
docker-compose up -d --build
```

## Kubernetes Commands

### Basic Commands

```bash
# Get resources
kubectl get pods
kubectl get services
kubectl get deployments
kubectl get nodes
kubectl get all --all-namespaces

# Describe resources
kubectl describe pod <pod-name>
kubectl describe service <service-name>

# Create resources from file
kubectl apply -f <filename.yaml>

# Delete resources
kubectl delete pod <pod-name>
kubectl delete -f <filename.yaml>

# Get logs
kubectl logs <pod-name>
kubectl logs -f <pod-name>  # Follow logs
```

### Advanced Commands

```bash
# Port forwarding
kubectl port-forward <pod-name> 8080:80

# Execute command in pod
kubectl exec -it <pod-name> -- /bin/bash

# Scale deployment
kubectl scale deployment <deployment-name> --replicas=3

# View rollout status
kubectl rollout status deployment/<deployment-name>

# Rollback deployment
kubectl rollout undo deployment/<deployment-name>

# Create namespace
kubectl create namespace <namespace-name>

# Set context namespace
kubectl config set-context --current --namespace=<namespace-name>
```

## CI/CD Concepts

### GitLab CI/CD

```yaml
# Basic .gitlab-ci.yml structure
stages:
  - build
  - test
  - deploy

build_job:
  stage: build
  script:
    - echo "Building the application"
    - docker build -t myapp:$CI_COMMIT_SHA .

test_job:
  stage: test
  script:
    - echo "Running tests"
    - docker run myapp:$CI_COMMIT_SHA npm test

deploy_job:
  stage: deploy
  script:
    - echo "Deploying application"
  only:
    - master
```

### GitHub Actions

```yaml
# Basic GitHub Actions workflow
name: CI/CD Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Build the application
        run: |
          echo "Building the application"
          docker build -t myapp:$GITHUB_SHA .

  test:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: |
          echo "Running tests"
          npm test
```

## Linux Commands

### File Management

```bash
# List files
ls -la

# Change directory
cd /path/to/directory

# Create directory
mkdir new_directory

# Create file
touch new_file.txt

# Remove file/directory
rm file.txt
rm -r directory/

# Copy files
cp source.txt destination.txt
cp -r source_dir/ destination_dir/

# Move files
mv source.txt destination.txt
```

### System Management

```bash
# Check disk space
df -h

# Check memory usage
free -m

# Check running processes
ps aux
ps aux | grep <process-name>

# View system resources
top
htop  # Install with apt/yum if not available

# Find files
find /path/to/search -name "filename"

# File permissions
chmod 755 script.sh
chown user:group file.txt
```

### Network Commands

```bash
# Check network interfaces
ifconfig
ip addr show

# Test connectivity
ping google.com

# View open ports
netstat -tulpn
ss -tulpn

# DNS lookup
nslookup example.com
dig example.com

# Download files
wget https://example.com/file.zip
curl -O https://example.com/file.zip

# SSH
ssh user@server
ssh-keygen -t rsa -b 4096  # Generate SSH key
```

## Bash Scripting Tips

### Basic Script Structure

```bash
#!/bin/bash

# Variables
NAME="DevOps"
echo "Hello, $NAME!"

# Conditionals
if [ "$NAME" == "DevOps" ]; then
    echo "Name is DevOps"
else
    echo "Name is not DevOps"
fi

# Loops
for i in {1..5}; do
    echo "Number: $i"
done

# While loop
count=0
while [ $count -lt 5 ]; do
    echo "Count: $count"
    ((count++))
done

# Functions
function greet {
    echo "Hello, $1!"
}
greet "World"
```

### Useful Scripting Tips

```bash
# Exit on error
set -e

# Debug mode
set -x

# Read user input
read -p "Enter your name: " user_name
echo "Hello, $user_name!"

# Command substitution
current_date=$(date +%Y-%m-%d)
echo "Today is $current_date"

# Error handling
if ! command -v docker &> /dev/null; then
    echo "Docker is not installed!"
    exit 1
fi

# Parse command line options
while getopts ":a:b:" opt; do
  case $opt in
    a) a_arg="$OPTARG";;
    b) b_arg="$OPTARG";;
    \?) echo "Invalid option -$OPTARG" >&2;;
  esac
done
```

## Cloud CLI Commands

### AWS CLI

```bash
# S3 commands
aws s3 ls
aws s3 cp file.txt s3://bucket-name/
aws s3 sync local_dir/ s3://bucket-name/remote_dir/

# EC2 commands
aws ec2 describe-instances
aws ec2 start-instances --instance-ids i-12345678
aws ec2 stop-instances --instance-ids i-12345678

# ECS commands
aws ecs list-clusters
aws ecs list-services --cluster cluster-name

# CloudFormation
aws cloudformation deploy --template-file template.yaml --stack-name my-stack
```

### Azure CLI

```bash
# Resource groups
az group list
az group create --name MyResourceGroup --location eastus

# VMs
az vm list
az vm create --resource-group MyResourceGroup --name MyVM --image UbuntuLTS --admin-username azureuser

# Storage
az storage account list
az storage account create --name mystorageaccount --resource-group MyResourceGroup
```

### Google Cloud CLI

```bash
# Compute instances
gcloud compute instances list
gcloud compute instances create my-instance --zone us-central1-a

# GKE
gcloud container clusters list
gcloud container clusters create my-cluster --zone us-central1-a

# Storage
gsutil ls
gsutil cp file.txt gs://bucket-name/
```

## Monitoring & Observability

### Prometheus

```bash
# Query examples for Prometheus
# CPU usage
rate(process_cpu_seconds_total[5m])

# Memory usage
process_resident_memory_bytes

# HTTP requests
rate(http_request_total[5m])

# Error rate
sum(rate(http_requests_total{status=~"5.."}[5m])) by (service) / sum(rate(http_requests_total[5m])) by (service)
```

### Grafana Dashboard JSON Example

```json
{
	"annotations": {
		"list": []
	},
	"editable": true,
	"fiscalYearStartMonth": 0,
	"graphTooltip": 0,
	"id": 1,
	"links": [],
	"liveNow": false,
	"panels": [
		{
			"datasource": "Prometheus",
			"fieldConfig": {
				"defaults": {
					"color": {
						"mode": "palette-classic"
					}
				},
				"overrides": []
			},
			"gridPos": {
				"h": 8,
				"w": 12,
				"x": 0,
				"y": 0
			},
			"options": {
				"legend": {
					"calcs": [],
					"displayMode": "list",
					"placement": "bottom",
					"showLegend": true
				},
				"tooltip": {
					"mode": "single",
					"sort": "none"
				}
			},
			"targets": [
				{
					"datasource": "Prometheus",
					"expr": "rate(process_cpu_seconds_total[5m])",
					"interval": "",
					"legendFormat": "CPU Usage",
					"refId": "A"
				}
			],
			"title": "CPU Usage",
			"type": "timeseries"
		}
	],
	"refresh": "5s",
	"schemaVersion": 37,
	"style": "dark",
	"tags": [],
	"templating": {
		"list": []
	},
	"time": {
		"from": "now-1h",
		"to": "now"
	},
	"timepicker": {},
	"timezone": "",
	"title": "System Dashboard",
	"version": 0
}
```

## Security Best Practices

### SSH Hardening

```bash
# Edit SSH config
sudo nano /etc/ssh/sshd_config

# Recommended settings
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys
Protocol 2
PermitEmptyPasswords no
MaxAuthTries 3
ClientAliveInterval 300
ClientAliveCountMax 0

# Restart SSH service
sudo systemctl restart sshd
```

### Firewall Setup (UFW)

```bash
# Allow SSH
sudo ufw allow 22/tcp

# Allow web traffic
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# Enable firewall
sudo ufw enable

# Check status
sudo ufw status
```

### Container Security

```bash
# Run container as non-root user
docker run -u 1000 nginx

# Scan images for vulnerabilities
docker scan myimage:latest

# Set resource limits
docker run --memory="256m" --cpus="0.5" nginx
```

## Terraform Commands

```bash
# Initialize working directory
terraform init

# Format code
terraform fmt

# Validate configuration
terraform validate

# Create execution plan
terraform plan

# Apply changes
terraform apply

# Destroy resources
terraform destroy

# Import existing resources
terraform import aws_instance.example i-12345678

# Show state
terraform state list
terraform state show aws_instance.example
```

## Ansible Commands

```bash
# Run playbook
ansible-playbook playbook.yml

# Run adhoc command
ansible all -m ping
ansible webservers -m command -a "uptime"

# List hosts
ansible all --list-hosts

# Check syntax
ansible-playbook --syntax-check playbook.yml

# Run with variables
ansible-playbook playbook.yml -e "variable_name=value"
```

---

This cheat sheet is meant to be a reference guide and not an exhaustive resource. Always refer to the official documentation for the most accurate and up-to-date information.
