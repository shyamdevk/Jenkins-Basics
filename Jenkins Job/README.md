# JENKINS JOBS

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
