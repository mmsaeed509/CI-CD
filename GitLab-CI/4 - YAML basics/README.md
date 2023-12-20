# YAML Basics

YAML (YAML Ain't Markup Language) is a human-readable data serialization format. It is commonly used for configuration files and data exchange between languages with different data structures. YAML files use indentation to represent the structure of data, making it easy to read and write.

### Basics

#### 1. Scalars

Scalars are the simplest YAML entities, representing basic values like strings, numbers, and booleans.

```yaml
name: John Doe
age: 30
is_student: false
```

#### 2. Lists

Lists are ordered collections of values.

```yaml
fruits:
  - apple
  - banana
  - orange
```

#### 3. Maps

Maps are unordered collections of key-value pairs.

```yaml
person:
  name: Alice
  age: 25
  city: Wonderland
```

#### 4. Nested Structures

YAML allows nesting of lists and maps.

```yaml
employees:
  - name: Bob
    position: Developer
  - name: Alice
    position: Designer
```

#### 5. Multi-line Strings

Multi-line strings can be represented using the `|` or `>` indicators.

```yaml
description: |
  This is a multi-line
  YAML string.
```

### Use Cases

#### 1. Configuration Files

YAML is widely used for configuration files due to its readability.

```yaml
# database.yaml
database:
  host: localhost
  port: 5432
  username: user
  password: secret
```

#### 2. Docker Compose

Docker Compose uses YAML for defining multi-container Docker applications.

```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: mysecretpassword
```

#### 3. Kubernetes

Kubernetes' configuration files, known as YAML manifests, describe deployment configurations.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

#### 4. Data Serialization

YAML is used to serialize and deserialize data between different programming languages.

```yaml
# Python
import yaml

data = {'name': 'John', 'age': 25}
yaml_data = yaml.dump(data)
```

YAML's simplicity and readability make it a versatile choice for various scenarios, from configuration files to data exchange formats.

---

# YAML Basics for GitLab CI

GitLab CI/CD (Continuous Integration/Continuous Deployment) uses YAML for configuring pipelines and jobs. Below are the basics of writing GitLab CI YAML files.

### 1. Stages and Jobs

Define stages and jobs for your CI pipeline.

```yaml
stages:
  - build
  - test
  - deploy

job_build:
  stage: build
  script:
    - echo "Building the project..."

job_test:
  stage: test
  script:
    - echo "Running tests..."

job_deploy:
  stage: deploy
  script:
    - echo "Deploying the application..."
```

### 2. Variables

Declare variables for reuse across jobs.

```yaml
variables:
  APP_NAME: myapp
  ENVIRONMENT: production

job_build:
  script:
    - echo "Building $APP_NAME for $ENVIRONMENT"
```

### 3. Artifacts

Define artifacts to pass between jobs.

```yaml
job_build:
  script:
    - echo "Building..."
  artifacts:
    paths:
      - build/
```

### 4. Dependencies

Specify dependencies between jobs.

```yaml
job_test:
  script:
    - echo "Running tests..."

job_deploy:
  script:
    - echo "Deploying..."
  dependencies:
    - job_test
```

### 5. Conditional Execution

Execute jobs conditionally based on variables or other factors.

```yaml
job_deploy:
  script:
    - echo "Deploying..."
  only:
    - master
```

### 6. Docker Images

Use Docker images for jobs.

```yaml
image: node:14

job_build:
  script:
    - npm install
    - npm run build
```

### 7. Services

Run additional services alongside the main job.

```yaml
services:
  - postgres:latest

job_test:
  script:
    - echo "Running tests with PostgreSQL..."
```

### 8. Caching

Cache dependencies to speed up builds.

```yaml
job_build:
  script:
    - echo "Building..."
  cache:
    paths:
      - node_modules/
```

### 9. Scripts

Run custom scripts within jobs.

```yaml
job_custom_script:
  script:
    - ./custom_script.sh arg1 arg2
```

These are just basic examples; GitLab CI YAML allows for extensive customization and integration with various tools to automate your CI/CD workflows efficiently.
