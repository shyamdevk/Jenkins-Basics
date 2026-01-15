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

