# Technical-Discussion
Use Jupyter Notebook to practice your repeatable technical documentation skills.

## About Exercise

Applicable to Data Science, Data Engineering, AI or Application Development.

### Key Terms

**Artifact** - The output of a build process, usually some file(s) that get deployed or released if tests pass. Artifacts represent the state of the code at a point in time.

**Build Server** - Automated server that runs tests and deployments when code is committed to source control.

**Collaborative Climate** - Environment where team members support each other, insights are valued, and successes are shared.

**Competent Team Members** - Each member has the required skills and expertise to excel in their role and contribute toward the goal.

**Elastic Beanstalk** - An AWS PaaS service used for deploying and scaling web applications by handling infrastructure provisioning and management.

**Infrastructure as Code** - Managing infrastructure in code for simplified provisioning and configuration.

**Jupyter Notebook** - Web-based interactive computing environment. Combines code, outputs, visualizations, and documentation in shareable notebook documents.

**Kaizen** - Japanese business philosophy focused on continuous improvement through gradual, incremental steps.

**Linting** - Analyzing code for potential errors, formatting issues, stylistic inconsistencies and suspicious constructs. Helps enforce standards and avoid mistakes.

**Metal as a Service** - Cloud model where physical bare-metal servers can be provisioned on demand instead of virtual machines. Useful for workloads requiring high performance hardware.

**Platform as a Service (PaaS)** - Cloud platform that abstracts and manages infrastructure like servers and storage so developers can build applications without configuring the underlying infrastructure.

**Principaled Leadership** - Manager leads in an ethical manner and serves as a role model in terms of character and conduct.

**Serverless** - An architecture where applications are hosted on managed infrastructure that runs code on-demand without needing to provision servers.

**Serverless Computing** - Executing application logic without provisioning servers. The cloud provider dynamically allocates resources only when a function or application is invoked.

**Software as a Service (SaaS)** - Cloud-based software that is licensed on a subscription basis. Users can access the software over the internet without needing to install or maintain it.

**Source Control** - Version control system to track changes to source code over time. Used to store infrastructure as code.

**Snowflake Server** - A manually configured server that lacks documentation of changes. Hard to replicate or rebuild.

**Static Website** - A website with content hosted on a storage service like S3 that is served directly to users without dynamic server-side processing.

**Virtual Machine** - An emulation of a computer system implemented in software that provides the functionality of a physical machine.

**Virtualization** - Abstracting compute resources from the underlying physical hardware to improve utilization and flexibility. Allows multiple virtual machines to run on one server.

## Code Snippets

### Markdown

> Use Markdown files for exercise documentation

A lightweight markup language used to format plain text documents. Allows for bold text, headers, lists, code blocks, image, etc. This whole document is markdown.

```Python
echo "# Heading 1" > test.md
echo "## Q1 Goals" > quarterly_plan.md
```

**requirements.txt** - A file listing all Python package dependencies needed for a project. Allows easily replicating environment and managing versions.

```Text
pylint==2.5.0
pytest==7.2.0
```

```Python
# Installs all packages in requirements.txt
pip install -r requirements.txt
```

### Gist

A simplistic way to share code snippets and fragments with others using Github.

```Python
import requests

url = "https://api.github.com/gists/gist_id"

response = requests.get(url)
print(response.json()["description"])
```

### Github

Web-based platform for version control and collaboration. Allows sharing and discussing code.

```Python
import github

# Authenticate and access GitHub API
g = github.Github("my_access_token")

repo = g.get_repo("user/repo")
print(repo.description)
```

**gcloud** - Command line tool for deploying and managing Google Cloud resources. Provides access to services like deployment, databases, storage.

```Python
gcloud app deploy # Deploys an App Engine application
gcloud sql databases create mydb # Creates Cloud SQL database  
gcloud auth login # Authenticates gcloud CLI
```

**Azure App Service** - Serverless web hosting in Azure to host web apps built with languages like Python. Scales without server management. Integrates with Azure Pipelines.

```Python
# Import Flask to create web app
from flask import Flask  

# Create Flask app
app = Flask(__name__)

# Define route for web app home page  
@app.route("/")
def home():
    return "Continuous Delivery to Azure App Service!"
```

**Azure Pipelines** - Azure service that provides continuous integration and delivery using YAML pipelines that link to source code repositories like GitHub. Automates build, test, and deploy steps.

```Python
# Example Azure pipeline YAML to build app

trigger:
- main

pool:
  vmImage: ubuntu-latest

steps:
- script: python -m flask run
  displayName: 'Run Flask app'
```

**cloud build** - Google Cloud Build is a service that executes workflow steps to build, test, and deploy applications. Workflows are defined in YAML files.

**app.yaml** - A configuration file that specifies how an application should be deployed and run on Google App Engine. Defines the runtime, handlers, and other settings.

**YAML**: A human-readable structured data format commonly used for configuration files. GitHub Actions workflows are defined in YAML files.

```YAML
# GitHub Actions Workflow YAML

name: CI
on: [push]

jobs:

  lint:
    runs-on: ubuntu-latest
    steps:
    
    - uses: actions/checkout@v3
    
    - name: Set up Python  
      uses: actions/setup-python@v3 
      with:
        python-version: "3.9"
        
    - name: Install 
      run: |
        pip install black
   
    - name: Lint
      run: | 
        black . --check
```

### Reproducible Code

Code that produces the same results when executed. Supports documentation and sharing of technical discussions.

```Python
# Function with reproducible result  
def add(a, b):
    return a + b

print(add(2, 3)) # Always prints 5
```

### Continuous Delivery

Software engineering practice to build, test, and release software rapidly, reliably, and sustainably. Each change flows through a pipeline with build, test, and deploy gates.

```Python
import ci_cd

pipeline = ci_cd.create_pipeline()

pipeline.build()
pipeline.test()
pipeline.deploy() # Continuous Delivery
```

### Continuous Integration

The practice of frequently merging developer code changes into a shared repository and automatically testing the changes to catch issues early.

```Python
# Continuous Integration 
import unittest

# New code change 
def sum(a, b):
    return a + b

# Test for validation  
class TestSum(unittest.TestCase):
    def test_sum(self):
        self.assertEqual(sum(2, 3), 5)

if __name__ == '__main__':
    unittest.main()

# If test passes, CI/CD pipeline continues
# If test fails, pipeline is blocked
```

### Automated Testing

Tests that run automatically without human input to verify software functionality and correctness.

```Python
import unittest

class TestSum(unittest.TestCase):

    def test_sum(self):
        self.assertEqual(sum([1, 2, 3]), 6)
        
if __name__ == '__main__':
    unittest.main() # Automated test
```

**Makefile**: A file containing recipes for common project automation tasks like installing dependencies, running tests, linting code, etc. Makefiles are commonly used with CI/CD pipelines.

```Makefile  
# Example Makefile recipe

lint:
    pylint **/*.py
test:  
    pytest -vv 
format:
    black *.py
clean:
    rm -rf build

# Call with `make lint` etc
```

**idempotence** - Ability to apply an operation multiple times without changing the result. Makes workflows more robust to failure by allowing replay without risk.

```Python
def set_flag(flag):
    # Sets flag to True no matter current value  
    flag = True
    print(f'Flag is now {flag}')
    
flag1 = True 
flag2 = False

set_flag(flag1) # Flag is now True  
set_flag(flag1) # Flag is now True - Idempotent

set_flag(flag2) # Flag is now True

## Cloud Build retries builds if they fail to improve reliability.

def create_resource():
    # Creates resource only if it does not exist
    if not resource_exists():  
        print("Creating new resource")
        # create resource

create_resource() # Creates resource
create_resource() # Idempotent, no-op
```

**Microservices** - Building applications from small, independent services that work together.

```Python
from flask import Flask
app = Flask(__name__)

@app.route('/hello')
def hello():
    return "Hello World!" 

if __name__ == '__main__':
    app.run() 
```

**modularity** - Breaking a system into logical components with clearly defined inputs/outputs. Allows reuse, testing and updating of individual modules.

```Python
# calculator.py module

def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

```

```Python
# Importing calculator module
import calculator

x = 5
y = 3

# Calling add function from external module  
print(calculator.add(x, y)) 

# Enables reusing logic in a modular way
```

**trigger** - Event listener that invokes an automated workflow when configured conditions are met, like a version control push.

```Python
import os
from functools import wraps

def on_new_commit(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        # Checks if commit hash changed
        if cache.get_commit() != os.getenv("GITHUB_SHA"):  
            func(*args, **kwargs)
    return wrapper

@on_new_commit
def deploy_app(*args):
   print("Deploying application")
```

**Serverless** - An architecture where applications are hosted on managed infrastructure that runs code on-demand without needing to provision servers.

```Python
# AWS Lambda handler
def handler(event, context):
    print("Hello from Lambda!")

# AWS Lambda is a rapidly evolving service, and the UX and development environments will always be moving targets to cover in a course.  The concepts are what matters. First, Cloud-based development environments are ideal for developing them, whether Cloud9 or CodeCatalyst. Second, AWS Lambda is a function that triggers in response to an event.  If UX changes to the console occur, remember these two core concepts.
```

**Static Website** - A website with content hosted on a storage service like S3 that is served directly to users without dynamic server-side processing.

```Python
# Upload static website to S3 bucket 
import boto3

s3 = boto3.client('s3')
s3.upload_file('index.html', 'my-bucket', 'index.html')
```

**Virtual Machine** - An emulation of a computer system implemented in software that provides the functionality of a physical machine.

```Python
# Provision EC2 instance
aws ec2 run-instances --image-id ami-abcd1234 --count 1 --instance-type t2.micro
```

**Infrastructure as Code** - Treating infrastructure configuration as software code that is version controlled and deployable. Allows repeatable, automated environment set up.

```Python
# Infrastructure as Code
infrastructure = {
    "load_balancer": "lb-1234", 
    "instances": ["server1", "server2"],
    "storage": "data_bucket" 
}

print(infrastructure) # Print configured infrastructure
```

**Cloud Environment** - A set of cloud-based resources like compute, storage, networking that host an application. Configured via infrastructure as code.

```Python
# Cloud Environment 
import boto3

ec2 = boto3.client('ec2')
response = ec2.run_instances(
    ImageId="ami-abcd1234",
    MinCount=1, 
    MaxCount=2
)

print(response) # Launch EC2 instances in AWS 
```

**Platform as a Service (PaaS)** - A cloud model that provides services to deploy applications without managing the underlying infrastructure.

```Python
# Deploy app to Elastic Beanstalk
import eb

app = eb.create_environment()
app.deploy(my_application)
```

**Elastic Beanstalk** - An AWS PaaS service used for deploying and scaling web applications by handling infrastructure provisioning and management.

```Python
import eb

app = eb.create_app("FlaskApp")
app.deploy()
app.scale(5) # Add 5 instances
```

**Elasticity** - The ability to automatically scale computing resources up and down based on demand.

```Python
# Scale EC2 instances based on load
import autoscaler

asg = autoscaler.create("my-asg")
asg.scale_up() # Add instances
asg.scale_down() # Remove instances
```

**Availability** - The proportion of time a system is operational and accessible.

```Python
import monitor

avail = monitor.check("my-service")
print(f"Service was available {avail * 100}% over the last month")
```

**Self-Service** - The ability for users to provision resources without going through IT.

```Python
# Provision AWS resources via CLI 
aws ec2 run-instances --image-id ami-abcd1234 --count 1
```

**Reduced Complexity** - Abstract infrastructure management from organizations so they can focus on core apps.

```Python
import ml

model = ml.train("my_algorithm") # Don't manage ML infrastructure
print(model.predict(x))
```

**Monitoring & Logging** - Tracking application and system metrics to diagnose problems.

```Python
import logging

logger = logging.getLogger(__name__)

logger.error("Database connection failed") 

# Sends error to logging system
```

---
