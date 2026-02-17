# JENKINS + GITHUB INTEGRATION
![Jenkins](https://github.com/shyamdevk/Jenkins-Basics/blob/images/git.gif)

This phase connects **code (GitHub)** with **automation (Jenkins)**.

---

## 🔹 Why Jenkins + GitHub?

In real projects:
- Code lives in GitHub
- Jenkins automatically builds code
- No manual build trigger

📌 This is **core CI** functionality.

---

## 🔹 How Jenkins Integrates with GitHub

Jenkins connects to GitHub using:
- Repository URL
- Credentials (token)
- Webhooks

---

## 🔹 Jenkins Credentials (IMPORTANT)

Jenkins stores GitHub:
- Username
- Personal Access Token (PAT)

✔ Secure storage  
❌ No hard-coding credentials

---

## 🔹 GitHub Webhooks

A **Webhook**:
- Notifies Jenkins when code changes
- Automatically triggers jobs

📌 Faster and better than polling.

---

## 🔬 LAB 6: Jenkins + GitHub Integration (Freestyle Job)

### 🎯 Objective
Automatically trigger Jenkins when code is pushed to GitHub.

---

### 🪜 Step-by-Step Instructions

#### Step 1: Create GitHub Token
1. GitHub → Settings → Developer Settings
2. Personal Access Token → Generate
3. Copy the token

---

#### Step 2: Add Credentials in Jenkins
1. Jenkins → Manage Jenkins
2. Credentials → Global → Add Credentials
3. Type: **Username with password**
4. Username: GitHub username
5. Password: GitHub token
6. Save

---

#### Step 3: Create Freestyle Job
1. New Item → Freestyle project
2. Source Code Management → Git
3. Add GitHub repo URL
4. Select credentials
5. Build Step:
   ```bash
   echo "GitHub integrated with Jenkins"

---

#### Step 4: Enable Webhook Trigger

1. Enable **GitHub hook trigger**
2. Save job

---

#### Step 5: Configure Webhook in GitHub

1. Repo → Settings → Webhooks
2. Payload URL:

   ```
   http://<jenkins-ip>:8080/github-webhook/
   ```
3. Content type: `application/json`
4. Save

---

### ✅ Expected Result

* Push code to GitHub
* Jenkins job runs automatically

---

## 🔬 LAB 7: Jenkins + GitHub (Pipeline Job)

### 🎯 Objective

Trigger pipeline using GitHub webhook.

---

### Jenkinsfile Example

```groovy
pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/your/repo.git'
      }
    }
    stage('Build') {
      steps {
        echo 'Pipeline triggered by GitHub'
      }
    }
  }
}
```

---

### ✅ Skills You Learn

✔ GitHub webhook
✔ Jenkins credentials
✔ Automated CI pipeline

---

# 📌 PHASE 5: JENKINS + BUILD TOOLS (MAVEN)

This phase focuses on **building applications** using Jenkins.

---

## 🔹 What is Maven?

**Maven** is a build tool used for:

* Compiling Java code
* Running tests
* Creating packages (JAR/WAR)

📌 Widely used in enterprise projects.

---

## 🔹 Why Jenkins + Maven?

* Automate Java builds
* Standard CI process
* Used in interviews frequently

---

## 🔹 Maven Lifecycle (Simple)

```
compile → test → package
```

---

## 🔹 Jenkins + Maven Flow

```
GitHub → Jenkins → Maven Build → Artifact
```

---

## 🔬 LAB 8: Jenkins + Maven Build (Freestyle Job)

### 🎯 Objective

Build a Java project using Maven in Jenkins.

---

### 🪜 Step-by-Step Instructions

#### Step 1: Install Maven Plugin

1. Jenkins → Manage Jenkins
2. Plugins → Maven Integration Plugin
3. Install

---

#### Step 2: Configure Maven

1. Manage Jenkins → Global Tool Configuration
2. Add Maven
3. Save

---

#### Step 3: Create Freestyle Job

1. New Item → Freestyle project
2. Git → Add Java project repo
3. Build Step → Invoke top-level Maven targets
4. Goals:

   ```
   clean package
   ```

---

### ✅ Expected Output

* Maven build runs
* `.jar` or `.war` file created

---

## 🔬 LAB 9: Jenkins + Maven Pipeline (RECOMMENDED)

### 🎯 Objective

Build Java project using Pipeline.

---

### Jenkinsfile Example

```groovy
pipeline {
  agent any
  tools {
    maven 'Maven'
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/your/java-repo.git'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
  }
}
```

## 🧠 Interview Quick Notes

* Webhooks trigger Jenkins automatically
* Jenkins stores GitHub credentials securely
* Maven builds Java applications
* Pipelines are preferred over freestyle jobs

---

# 🚀 Jenkins Learning Notes – Phase 6 & Phase 7

> These phases move you from **CI** to **real DevOps pipelines**  
> Jenkins + Docker + Kubernetes = 💯 Job-ready skillset

---

# JENKINS + DOCKER

![Jenkins](https://github.com/shyamdevk/Jenkins-Basics/blob/images/jendock.webp)

This phase teaches **container-based CI/CD**, which is **VERY IMPORTANT**.

---

## 🔹 Why Jenkins + Docker?

Problems without Docker:
- Works on my machine issue
- Different environments
- Dependency conflicts

Docker solves this by:
✔ Packaging app + dependencies  
✔ Same environment everywhere  
✔ Faster builds  

---

## 🔹 Jenkins + Docker Workflow

```

GitHub → Jenkins → Build Docker Image → Push to Registry

````

---

## 🔹 Requirements (Before Lab)

Make sure:
- Jenkins is installed
- Docker is installed on Jenkins server
- Jenkins user has Docker permission

Command:
```bash
sudo usermod -aG docker jenkins
sudo systemctl restart jenkins
````

---

## 🔬 LAB 10: Jenkins Build Docker Image (BASIC – MUST DO)

### 🎯 Objective

Build a Docker image using Jenkins Pipeline.

---

### 🪜 Step-by-Step Instructions

#### Step 1: Create Sample App

Create a file `app.sh`:

```bash
echo "Hello from Docker via Jenkins"
```

---

#### Step 2: Create Dockerfile

```Dockerfile
FROM alpine
COPY app.sh /app.sh
CMD ["sh", "/app.sh"]
```

---

#### Step 3: Create Jenkinsfile

```groovy
pipeline {
  agent any

  stages {
    stage('Build Docker Image') {
      steps {
        sh 'docker build -t jenkins-docker-demo .'
      }
    }

    stage('Run Container') {
      steps {
        sh 'docker run jenkins-docker-demo'
      }
    }
  }
}
```

---

### ✅ Expected Output

* Docker image built
* Container runs successfully
* Output visible in Jenkins console

---

## 🔬 LAB 11: Jenkins + Docker Hub (REAL WORLD)

![Jenkins](https://github.com/shyamdevk/Jenkins-Basics/blob/images/jenhub.gif)

### 🎯 Objective

Push Docker image to Docker Hub.

---

### 🪜 Steps

#### Step 1: Add Docker Hub Credentials

* Jenkins → Manage Jenkins → Credentials
* Add Username & Password

---

#### Step 2: Update Jenkinsfile

```groovy
pipeline {
  agent any

  stages {
    stage('Build Image') {
      steps {
        sh 'docker build -t <docker-username>/demo-app .'
      }
    }

    stage('Login to Docker Hub') {
      steps {
        withCredentials([usernamePassword(
          credentialsId: 'dockerhub',
          usernameVariable: 'USER',
          passwordVariable: 'PASS'
        )]) {
          sh 'docker login -u $USER -p $PASS'
        }
      }
    }

    stage('Push Image') {
      steps {
        sh 'docker push <docker-username>/demo-app'
      }
    }
  }
}
```

---

### ✅ Skills You Gain

✔ Docker build automation
✔ Secure credential usage
✔ Real CI/CD pipeline

---

# 📌 PHASE 7: JENKINS + KUBERNETES (INTRO LEVEL)

This phase introduces **cloud-native CI/CD**.

📌 **Foundation level is enough for freshers**

---

## 🔹 Why Jenkins + Kubernetes?

Kubernetes allows:

* Dynamic build agents
* Auto scaling
* Faster & isolated builds

📌 Jenkins creates **pods on demand**.

---

## 🔹 Jenkins + Kubernetes Architecture (Simple)

```
Jenkins → Kubernetes API → Pod Created → Job Runs → Pod Deleted
```

---

## 🔹 Kubernetes as Jenkins Agent

* Jenkins does NOT run jobs itself
* It requests Kubernetes to create pods
* Pods act as agents

---

## 🔬 LAB 12: Jenkins with Kubernetes Agent (BASIC)

### 🎯 Objective

Run Jenkins pipeline inside Kubernetes pod.

---

### 🪜 Requirements

* Kubernetes cluster (Minikube is enough)
* Jenkins Kubernetes plugin installed

---

### 🪜 Step-by-Step Instructions

#### Step 1: Install Kubernetes Plugin

* Manage Jenkins → Plugins
* Install **Kubernetes plugin**

---

#### Step 2: Configure Kubernetes Cloud

* Manage Jenkins → Clouds → Kubernetes
* Add:

  * Kubernetes URL
  * Namespace
  * Jenkins URL

---

#### Step 3: Sample Kubernetes Pipeline

```groovy
pipeline {
  agent {
    kubernetes {
      yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: alpine
    image: alpine
    command:
    - cat
    tty: true
"""
    }
  }

  stages {
    stage('Run in Pod') {
      steps {
        container('alpine') {
          sh 'echo Hello from Kubernetes Agent'
        }
      }
    }
  }
}
```

---

### ✅ Expected Output

* Kubernetes pod created
* Command executed inside pod
* Pod destroyed after job

---

## 🎯 Minimum Labs to Complete

| Phase      | Lab         | Mandatory |
| ---------- | ----------- | --------- |
| Docker     | Build Image | ✅         |
| Docker     | Push Image  | ✅         |
| Kubernetes | Pod Agent   | ✅         |

---

## 🧠 Interview Quick Notes (VERY IMPORTANT)

* Docker ensures consistent environments
* Jenkins automates Docker builds
* Kubernetes provides dynamic agents
* Pods are created per job
* Pipelines are preferred over freestyle


