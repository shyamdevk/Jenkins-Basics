# 🚀 Jenkins Basics

![Jenkins](https://github.com/shyamdevk/Jenkins-Basics/blob/images/jen.gif)

## 📌 PHASE 0: CI/CD FOUNDATION (Quick Basics)

Before learning Jenkins, you must understand **why Jenkins is needed**.

---

## 🔹 What is CI/CD?

**CI/CD** stands for:

- **CI** – Continuous Integration  
- **CD** – Continuous Delivery / Continuous Deployment  

It is a process to **automatically build, test, and deploy code**.

---

### 🔁 Traditional Development (Without CI/CD)

1. Developer writes code
2. Code is sent manually to server
3. Errors appear late
4. Deployment takes more time
5. High chance of failure

❌ Slow  
❌ Error-prone  
❌ Manual work

---

### ✅ Modern Development (With CI/CD)

1. Developer pushes code to GitHub
2. CI tool automatically builds the code
3. Tests run automatically
4. Application is deployed automatically

✔ Fast  
✔ Reliable  
✔ Automated  

---

## 🔹 What is Continuous Integration (CI)?

**Continuous Integration** means:

- Developers frequently push code to a shared repository
- Every push triggers:
  - Build
  - Test
  - Code validation

📌 Goal: **Catch errors early**

Example:
```

git commit → git push → build → test

```

---

## 🔹 What is Continuous Delivery (CD)?

**Continuous Delivery** means:

- Code is always **ready for deployment**
- Deployment is done manually with one click

📌 Used when approval is needed before release

---

## 🔹 What is Continuous Deployment?

**Continuous Deployment** means:

- Code is deployed to production **automatically**
- No manual approval required

📌 Used in startups and fast-moving teams

---

## 🔹 Why Do We Need CI/CD?

| Problem | Solution |
|------|--------|
| Manual deployment | Automation |
| Late bug detection | Early testing |
| Slow releases | Faster releases |
| Human errors | Consistency |

---

## 🔹 Common CI/CD Tools

- Jenkins
- GitHub Actions
- GitLab CI
- Azure DevOps
- CircleCI

👉 **Jenkins is one of the most widely used CI/CD tools**

---

## 📌 PHASE 1: JENKINS FUNDAMENTALS

Now let’s understand **Jenkins from scratch**.

---

## 🔹 What is Jenkins?

**Jenkins** is an **open-source automation server** used to:

- Build applications
- Test applications
- Deploy applications

📌 Jenkins automates **CI/CD pipelines**

---

## 🔹 Why Jenkins is Popular?

✔ Free and open-source  
✔ Huge plugin ecosystem  
✔ Easy to integrate with tools  
✔ Industry standard  
✔ Strong community support  

---

## 🔹 Where Jenkins is Used?

- Web applications
- Mobile backends
- Cloud & DevOps projects
- Microservices
- Enterprise applications

---

## 🔹 Jenkins Architecture (Simple Explanation)

Jenkins works in **Master-Agent model**

![Jenkins](https://github.com/shyamdevk/Jenkins-Basics/blob/images/arch1.webp)

### 🧠 Jenkins Master
- Controls everything
- Manages jobs
- Schedules builds
- Provides UI

### 🏗 Jenkins Agent (Worker)
- Executes jobs
- Runs build tasks
- Can be multiple agents

📌 Master tells **WHAT to do**, Agent does **THE WORK**

# 🏗️ Jenkins Architecture – Detailed Model

![Jenkins](https://github.com/shyamdevk/Jenkins-Basics/blob/images/archi.gif)

---

## 📌 High-Level Idea

Jenkins follows a **Controller (Server) – Agent model**.

- **Jenkins Server** → Brain (controls everything)
- **Jenkins Agents** → Workers (do the actual job)

---

## 🧠 Jenkins Server (Controller)

The **Jenkins Server** is the **main machine**.

It is responsible for **managing**, **controlling**, and **coordinating** everything.

### 🔹 What Jenkins Server Contains

| Component | Simple Meaning |
|--------|---------------|
| Jobs | Instructions Jenkins must run |
| Users | People who access Jenkins |
| Plugins | Extra features for Jenkins |
| Nodes / Clouds | Agent configurations |
| Credentials | Passwords, tokens, SSH keys |
| Global Configs | System-wide settings |
| Jenkins Data | Logs, build history, configs |

📌 **Important:**  
Jenkins Server usually **does NOT do heavy work**.  
It only **assigns work to agents**.

---

## ⚙️ Jenkins Jobs

A **Job** tells Jenkins:
- What code to pull
- What command to run
- What pipeline to execute

Example:
```

Pull code → Build → Test → Deploy

```

---

## 👥 Users

Users are:
- Developers
- DevOps engineers
- Admins

They:
- Create jobs
- Trigger builds
- View logs

---

## 🔌 Plugins

Plugins extend Jenkins features.

Examples:
- Git plugin → pull code
- Docker plugin → build images
- Kubernetes plugin → create pods

📌 Jenkins becomes powerful **because of plugins**.

---

## 🔐 Credentials

Credentials store:
- GitHub tokens
- Docker Hub passwords
- SSH keys
- Cloud credentials

✔ Stored securely  
❌ Not written inside code

---

## ☁️ Nodes / Clouds

This is where **agents are defined**.

Jenkins supports:
- Static agents (always running)
- Dynamic agents (created when needed)

---

## 🧱 Jenkins Agents (Workers)

Agents are machines that **execute jobs**.

Jenkins supports **two types of agents**:

---

## 🟦 1. Static Agents (Always Running)

### 🔹 What are Static Agents?

- Always ON
- Pre-configured
- Long-running machines

Examples:
- Linux servers
- Windows servers

### 🔹 How They Connect?

- SSH
- WinRM
- JNLP

📌 Used when:
- Dedicated build servers are needed
- Long-running tasks exist

---

## 🟩 2. Dynamic Agents (Ephemeral / Cloud)

### 🔹 What are Dynamic Agents?

- Created **only when a job starts**
- Destroyed **after job completion**
- Save cost and resources

📌 Also called **Ephemeral Agents**

---

### 🔹 Types of Dynamic Agents

| Technology | Meaning |
|---------|--------|
| Docker | Containers used as agents |
| Kubernetes Pods | Pods created per build |
| AWS EC2 | Instances created on demand |
| AWS EKS | Kubernetes-based agents |

---

### 🔹 How Dynamic Agents Work

1. Job starts
2. Jenkins creates agent via API
3. Job runs on agent
4. Job completes
5. Agent is destroyed

✔ Fast  
✔ Cost-effective  
✔ Scalable  

---

## 🔁 Communication Between Server & Agents

| Method | Used For |
|-----|---------|
| SSH / WinRM | Static agents |
| JNLP | Agent-server connection |
| APIs | Cloud & dynamic agents |

📌 Jenkins Server **controls**, Agents **execute**.

---

## 🔄 Full Jenkins Workflow (Simple)

1. Developer pushes code to GitHub
2. Jenkins Server detects change
3. Jenkins selects an agent
4. Agent runs the job
5. Logs sent back to server
6. Job result stored in Jenkins

---

## 📦 Jenkins Data

Jenkins stores:
- Job configs
- Build logs
- Plugins
- User data

📌 Usually stored in:
```

/var/lib/jenkins

```

---

## 🎯 Key Points to Remember (Interview Ready)

- Jenkins uses **Controller–Agent model**
- Server manages, agents execute
- Static agents = always running
- Dynamic agents = created & destroyed
- Plugins extend Jenkins functionality
- Credentials are stored securely

---

## ✅ Summary

✔ Jenkins Server = Brain  
✔ Jenkins Agents = Workers  
✔ Jobs define tasks  
✔ Plugins add power  
✔ Dynamic agents save cost  

---
## 🔹 Jenkins Workflow (Step by Step)

1. Developer pushes code to GitHub
2. Jenkins detects the change
3. Jenkins pulls the code
4. Jenkins builds the project
5. Jenkins runs tests
6. Jenkins deploys the app

---

## 🔹 Jenkins Jobs

A **Job** is a task Jenkins performs.

Examples:
- Build a project
- Run tests
- Deploy application

Types:
- Freestyle Job
- Pipeline Job (modern & recommended)

---

## 🔹 Jenkins Plugins

Plugins add **extra features** to Jenkins.

Examples:
- Git plugin
- Docker plugin
- Maven plugin
- Kubernetes plugin

📌 Jenkins without plugins is incomplete

---

## 🔹 Jenkins Installation (Overview)

Basic steps:
1. Install Java
2. Install Jenkins
3. Start Jenkins service
4. Access Jenkins UI on port `8080`

Example:
```

http://<server-ip>:8080

```

---

## 🔹 Jenkins UI Overview

Main components:
- Dashboard
- Jobs list
- Build history
- Configure options
- Manage Jenkins

---

## 🔹 Jenkins Credentials

Jenkins stores:
- GitHub tokens
- Docker Hub credentials
- SSH keys

📌 Credentials are stored **securely**, not in code

---

## 🎯 Interview Quick Notes

- Jenkins is a **CI/CD tool**
- Jenkins automates **build, test, deploy**
- Jenkins uses **Master-Agent architecture**
- Jenkins supports **plugins**
- Jenkins jobs define tasks

---
Perfect 👍
Below is a **beginner-friendly, well-decorated `README.md`** covering **PHASE 2 (Jenkins Jobs)** and **PHASE 3 (Jenkins Pipelines)**.

Language is **simple**, **step-by-step**, and **interview-ready** — same style as your previous notes.

You can **directly copy-paste** this into your repo ✅

---

# 🚀 Jenkins Learning Notes – Phase 2 & Phase 3

> Beginner-friendly notes on **Jenkins Jobs** and **Jenkins Pipelines**  
> Written in **simple words** with **real-world understanding**

---

# 📌 PHASE 2: JENKINS JOBS

In this phase, you learn **how Jenkins actually runs tasks**.

---

## 🔹 What is a Jenkins Job?

A **Jenkins Job** is a **task or work** that Jenkins performs.

Examples:
- Build an application
- Run tests
- Deploy code
- Execute scripts

📌 Jenkins does nothing without jobs.

---

## 🔹 Types of Jenkins Jobs

| Job Type | Purpose |
|-------|--------|
| Freestyle Job | Simple & basic jobs |
| Pipeline Job | Advanced & modern CI/CD |
| Multibranch Pipeline | Multiple branches support |
| Folder Job | Organize jobs |

👉 As a beginner, **focus on Freestyle & Pipeline jobs**.

---

## 🟦 Freestyle Job (Beginner Level)

### 🔹 What is a Freestyle Job?

- Oldest job type in Jenkins
- GUI-based (click and configure)
- Easy to create
- Limited flexibility

📌 Good for **learning basics**

---

### 🔹 Freestyle Job Components

1. Source Code Management (Git)
2. Build Triggers
3. Build Steps
4. Post-build Actions

---

### 🔹 Freestyle Job Flow

```

GitHub → Jenkins → Build → Test → Result

````

---

### 🔹 Build Triggers

Build triggers decide **WHEN** a job should run.

| Trigger | Meaning |
|------|-------|
| Build Manually | Click “Build Now” |
| Poll SCM | Check repo at intervals |
| GitHub Webhook | Auto build on push |
| Schedule (Cron) | Run at fixed time |

---

### 🔹 Build Steps

Build steps define **WHAT to execute**.

Examples:
- Execute shell command
- Run Maven build
- Run Python script

Example:
```bash
echo "Hello Jenkins"
````

---

### 🔹 Post-Build Actions

Actions after job completes:

* Email notification
* Archive artifacts
* Trigger another job

---

## ⚠️ Limitations of Freestyle Jobs

❌ Hard to manage
❌ No version control
❌ Not reusable
❌ Not suitable for complex pipelines

👉 That’s why **Pipelines were introduced**

## 🔬 LAB 1: Create Your First Freestyle Job (MUST DO)

### 🎯 Objective
Learn how to:
- Create a job
- Pull code from GitHub
- Run a simple command

---

### 🪜 Steps

1. Open Jenkins Dashboard
2. Click **New Item**
3. Select **Freestyle project**
4. Name: `freestyle-demo`
5. Under **Source Code Management**
   - Select **Git**
   - Add any GitHub repo URL
6. Under **Build Steps**
   - Select **Execute shell**
   - Add:
     ```bash
     echo "Hello from Jenkins Freestyle Job"
     ```
7. Save and click **Build Now**

---

### ✅ Expected Output
- Build status: **SUCCESS**
- Console output shows the message

---
## 🔬 LAB 2: Freestyle Job with GitHub Trigger

### 🎯 Objective
Automatically trigger Jenkins when code is pushed.

---

### 🪜 Steps

1. Edit your Freestyle job
2. Enable **GitHub hook trigger for GITScm polling**
3. In GitHub repo:
   - Add Jenkins webhook
4. Push a commit

---

### ✅ Expected Result
- Jenkins job starts automatically

---

# 📌 PHASE 3: JENKINS PIPELINES – PRACTICAL LABS

## 🔬 LAB 3: Create Your First Pipeline Job (MUST DO)

### 🎯 Objective
Understand:
- Pipeline job
- Jenkinsfile
- Declarative syntax

---

### 🪜 Steps

1. Click **New Item**
2. Select **Pipeline**
3. Name: `pipeline-demo`
4. In Pipeline section:
   - Choose **Pipeline script**
5. Add:
   ```groovy
   pipeline {
     agent any
     stages {
       stage('Hello') {
         steps {
           echo 'Hello from Jenkins Pipeline'
         }
       }
     }
   }
Save → Build Now

✅ Expected Output
Pipeline runs successfully

Output visible per stage

# 📌 PHASE 3: JENKINS PIPELINES (VERY IMPORTANT)

![Jenkins](https://github.com/shyamdevk/Jenkins-Basics/blob/images/pipe.gif)

---

## 🔹 What is a Jenkins Pipeline?

A **Pipeline** is a **series of automated steps** written as **code**.

📌 Pipeline = CI/CD as Code

---

## 🔹 Why Pipelines are Better?

✔ Stored in GitHub
✔ Easy to manage
✔ Version controlled
✔ Reusable
✔ Supports complex workflows

---

## 🔹 Jenkinsfile

A **Jenkinsfile**:

* Defines pipeline steps
* Written in Groovy syntax
* Stored inside project repo

File name:

```
Jenkinsfile
```

---

## 🔹 Types of Jenkins Pipelines

| Pipeline Type | Description         |
| ------------- | ------------------- |
| Declarative   | Simple & structured |
| Scripted      | Advanced & flexible |

👉 **Always start with Declarative Pipeline**

---

## 🟩 Declarative Pipeline (Recommended)

### 🔹 Basic Structure

```groovy
pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        echo 'Building application'
      }
    }
  }
}
```

---

## 🔹 Important Pipeline Keywords

| Keyword  | Meaning             |
| -------- | ------------------- |
| pipeline | Start of pipeline   |
| agent    | Where job runs      |
| stages   | Group of steps      |
| stage    | Single phase        |
| steps    | Commands to execute |
| post     | Actions after build |

---

## 🔹 Common Pipeline Stages

| Stage    | Purpose      |
| -------- | ------------ |
| Checkout | Pull code    |
| Build    | Compile code |
| Test     | Run tests    |
| Deploy   | Deploy app   |

---

## 🔹 Example CI Pipeline

```groovy
pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/example/repo.git'
      }
    }

    stage('Build') {
      steps {
        echo 'Build completed'
      }
    }

    stage('Test') {
      steps {
        echo 'Tests passed'
      }
    }
  }
}
```

---

## 🔹 Agent in Pipeline

Defines **where the pipeline runs**.

Examples:

```groovy
agent any
```

```groovy
agent {
  label 'linux'
}
```

---

## 🔹 Post Section

Runs **after pipeline finishes**.

```groovy
post {
  success {
    echo 'Build successful'
  }
  failure {
    echo 'Build failed'
  }
}
```

---

## 🔹 Multistage Pipeline Flow

```
Code Push → Checkout → Build → Test → Deploy
```
## 🎯 Interview Quick Notes

* Job = Task
* Freestyle = GUI-based
* Pipeline = Code-based
* Jenkinsfile defines pipeline
* Declarative pipeline is preferred
---
# 📌 PHASE 3: JENKINS PIPELINES – PRACTICAL LABS

## 🔬 LAB 3: Create Your First Pipeline Job (MUST DO)

### 🎯 Objective
Understand:
- Pipeline job
- Jenkinsfile
- Declarative syntax

---

### 🪜 Steps

1. Click **New Item**
2. Select **Pipeline**
3. Name: `pipeline-demo`
4. In Pipeline section:
   - Choose **Pipeline script**
5. Add:
   ```groovy
   pipeline {
     agent any
     stages {
       stage('Hello') {
         steps {
           echo 'Hello from Jenkins Pipeline'
         }
       }
     }
   }
Save → Build Now

✅ Expected Output
Pipeline runs successfully

Output visible per stage

🔬 LAB 4: Pipeline with Jenkinsfile (REAL WORLD)
🎯 Objective

Store pipeline as code in GitHub.

🪜 Steps

Create a file named Jenkinsfile in your GitHub repo

Add:

pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building from Jenkinsfile'
      }
    }
  }
}


Push code to GitHub

In Jenkins:

Create Pipeline job

Select Pipeline script from SCM

Add repo URL

✅ Expected Output

Jenkins pulls Jenkinsfile

Pipeline executes automatically

---

# 🚀 Jenkins Pipeline Lab (Step-by-Step)

## 📌 Objective

By the end of this lab, you will:

* Install Jenkins
* Create a Jenkins Pipeline job
* Write your **first Jenkinsfile**
* Run a simple CI pipeline (Build → Test → Deploy simulation)

> 👶 **Assumption:** You are completely new to Jenkins

---

## 🛠️ Prerequisites

* Linux system (Ubuntu / Amazon Linux / EC2)
* Java 11 or 17
* Internet access
* GitHub account

---

## 🔹 Step 1: Install Java (Required)

```bash
sudo apt update
sudo apt install -y openjdk-17-jdk
java -version
```

✅ Output should show Java version.

---

## 🔹 Step 2: Install Jenkins

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update
sudo apt install -y jenkins
```

Start Jenkins:

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

Check status:

```bash
sudo systemctl status jenkins
```

---

## 🔹 Step 3: Access Jenkins Web UI

Open browser:

```
http://<YOUR_SERVER_IP>:8080
```

Get initial admin password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

📌 Paste password → Click **Continue**

---

## 🔹 Step 4: Jenkins Initial Setup

1. Click **Install Suggested Plugins**
2. Create **Admin User**
3. Finish setup

✅ Jenkins dashboard will open

---

## 🔹 Step 5: Install Required Plugin

Go to:

```
Dashboard → Manage Jenkins → Plugins
```

Check & install:

* ✅ **Pipeline**

Restart Jenkins if asked.

---

## 🔹 Step 6: Create Sample GitHub Repository

Create a new GitHub repo:

```
jenkins-pipeline-lab
```

Clone it:

```bash
git clone https://github.com/<your-username>/jenkins-pipeline-lab.git
cd jenkins-pipeline-lab
```

---

## 🔹 Step 7: Create Jenkinsfile

Inside repo, create a file:

```bash
nano Jenkinsfile
```

Paste this **BEGINNER Jenkins Pipeline** 👇

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }
}
```

Save and exit.

---

## 🔹 Step 8: Push Code to GitHub

```bash
git add Jenkinsfile
git commit -m "Added first Jenkins pipeline"
git push origin main
```

---

## 🔹 Step 9: Create Jenkins Pipeline Job

1. Jenkins Dashboard → **New Item**
2. Name: `pipeline-lab`
3. Select: **Pipeline**
4. Click **OK**

---

## 🔹 Step 10: Configure Pipeline

Scroll to **Pipeline section**

* Definition: **Pipeline script from SCM**
* SCM: **Git**
* Repository URL:

  ```
  https://github.com/<your-username>/jenkins-pipeline-lab.git
  ```
* Branch:

  ```
  main
  ```
* Script Path:

  ```
  Jenkinsfile
  ```

Click **Save**

---

## 🔹 Step 11: Run the Pipeline 🎉

Click:

```
Build Now
```

Go to:

```
Build → Console Output
```

✅ You should see:

```
Building the application...
Running tests...
Deploying application...
```

🎉 **Your first Jenkins Pipeline is SUCCESSFUL**

---

## 📘 What You Learned

* What Jenkins Pipeline is
* How Jenkinsfile works
* Pipeline stages concept
* GitHub + Jenkins integration
* CI workflow basics

---

## 🔁 Practice Tasks (Very Important)

Try these:

1. Add a new stage called `Code Quality`
2. Replace `echo` with shell command:

   ```groovy
   sh 'ls -la'
   ```
3. Fail the pipeline intentionally:

   ```groovy
   sh 'exit 1'
   ```

---

## 🧠 Simple Pipeline Flow

```
Developer → GitHub → Jenkins → Build → Test → Deploy
```

# 🚀 Jenkins Pipeline + Shell Script (Beginner LAB)

## 📌 Objective

This lab helps beginners understand:

* How Jenkins runs **real Linux commands**
* How to use **Shell Scripts (`.sh`) inside Jenkins Pipeline**
* How pipelines **fail & succeed**
* How CI works in real DevOps projects

👶 *Assume you are new to Jenkins & Shell scripting*

---

## 🛠️ Prerequisites

* Jenkins installed & running
* Basic Linux terminal access
* GitHub account
* Jenkins Pipeline Plugin installed

---

## 🔹 Step 1: Create GitHub Repository

Create a new GitHub repository named:

```
jenkins-shell-pipeline-lab
```

Clone it:

```bash
git clone https://github.com/<your-username>/jenkins-shell-pipeline-lab.git
cd jenkins-shell-pipeline-lab
```

---

## 🔹 Step 2: Create a Shell Script

Create a folder:

```bash
mkdir scripts
cd scripts
```

Create a shell script:

```bash
nano build.sh
```

Paste this 👇

```bash
#!/bin/bash

echo "Starting Build Process..."
echo "Listing files:"
ls -la
echo "Build completed successfully"
```

Save and exit.

Make script executable:

```bash
chmod +x build.sh
```

---

## 🔹 Step 3: Create Jenkinsfile

Go back to project root:

```bash
cd ..
nano Jenkinsfile
```

Paste this **Beginner Pipeline** 👇

```groovy
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Running build script'
                sh 'bash scripts/build.sh'
            }
        }

        stage('Test') {
            steps {
                echo 'Running test commands'
                sh 'echo "Tests passed successfully"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy step (simulation)'
                sh 'echo "Application deployed"'
            }
        }
    }
}
```

Save and exit.

---

## 🔹 Step 4: Push Code to GitHub

```bash
git add .
git commit -m "Jenkins pipeline with shell script"
git push origin main
```

---

## 🔹 Step 5: Create Jenkins Pipeline Job

1. Jenkins Dashboard → **New Item**
2. Name: `jenkins-shell-lab`
3. Select: **Pipeline**
4. Click **OK**

---

## 🔹 Step 6: Configure Pipeline

In **Pipeline section**:

* Definition: `Pipeline script from SCM`
* SCM: `Git`
* Repository URL:

  ```
  https://github.com/<your-username>/jenkins-shell-pipeline-lab.git
  ```
* Branch:

  ```
  main
  ```
* Script Path:

  ```
  Jenkinsfile
  ```

Click **Save**

---

## 🔹 Step 7: Run the Pipeline ▶️

Click:

```
Build Now
```

Open:

```
Build → Console Output
```

### ✅ Expected Output

```
Starting Build Process...
Listing files...
Build completed successfully
Tests passed successfully
Application deployed
```

🎉 **Pipeline executed successfully**

---

## 🧠 What You Learned (Important)

* Jenkins can execute **Linux shell commands**
* `sh` is used to run shell scripts
* Jenkins pipeline executes steps **sequentially**
* Jenkins stops if a command fails
* Real CI uses scripts, not just `echo`

---

## 🔥 Important Concept (Very Exam/Interview Useful)

### ❓ What happens if a shell command fails?

Try this 👇
Edit `build.sh`:

```bash
exit 1
```

Run pipeline again.

🚨 Result:

* Pipeline **FAILS**
* Next stages **will not run**

✅ This is **real CI behavior**

---

## 🧪 Practice Tasks (Do These)

1️⃣ Add a new stage called `Code Quality`
2️⃣ Add command:

```groovy
sh 'pwd'
```

3️⃣ Print Jenkins workspace:

```groovy
sh 'ls $WORKSPACE'
```

---

## 📘 Simple Pipeline Flow

```
GitHub Code
   ↓
Jenkins pulls code
   ↓
Runs Shell Script
   ↓
Build → Test → Deploy
```

# 🚀 Jenkins Learning Notes – Phase 4 & Phase 5

> This phase focuses on **real-world Jenkins usage**  
> You will learn **GitHub integration** and **building applications**

---

# 📌 PHASE 4: JENKINS + GITHUB INTEGRATION

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


