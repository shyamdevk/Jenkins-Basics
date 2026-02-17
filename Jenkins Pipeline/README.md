# JENKINS PIPELINES – PRACTICAL LABS

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
