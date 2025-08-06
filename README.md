
# 🚀 Java Maven Project Deployment with Jenkins (Freestyle Project)

This repository demonstrates how to build and test a Java Maven project using Jenkins Freestyle jobs on an Ubuntu EC2 instance.

---

## 📁 Project Structure

```
.
├── pom.xml
└── src
    ├── main
    │   └── java
    │       └── com
    │           └── fortune
    │               └── myapp
    │                   └── App.java
    └── test
        └── java
            └── com
                └── fortune
                    └── myapp
                        └── AppTest.java
```

---

## 🌐 GitHub Setup

1. Push your code to GitHub:

```bash
git init
git remote add origin https://github.com/Smolke9/Jenkins-Maven-Project.git
git add .
git commit -m "Initial Maven Project Upload"
git branch -M main
git push -u origin main
```

2. Add webhook in GitHub:

- Go to: `Settings → Webhooks → Add webhook`
- Payload URL: `http://<Your-Jenkins-IP>:8080/github-webhook/`
- Content type: `application/json`
- Trigger: Push events

---

## 🔧 Jenkins Setup on Ubuntu EC2

### ✅ Java and Maven Installation (Ubuntu)

```bash
sudo apt update
sudo apt install openjdk-11-jdk maven -y
java -version
mvn -version
```

### 🔧 Configure Jenkins Tools

- Go to: `Manage Jenkins → Global Tool Configuration`
- Add Maven:
  - Name: `mymaven`
  - Uncheck "Install Automatically"

---

## 📦 Jenkins Freestyle Project – Build

### 1️⃣ Create Job: `maven-project`

- **Source Code Management**: Git → `https://github.com/Smolke9/Jenkins-Maven-Project.git`
- **Build Trigger**: GitHub hook trigger for GITScm polling
- **Build Step**: Invoke top-level Maven targets
  - Maven Version: `mymaven`
  - Goals: `clean package`

✅ Result: `BUILD SUCCESS`

---

## 🧪 Jenkins Freestyle Project – Test

### 2️⃣ Create Job: `maven-test`

- **Source Code Management**: Git → `https://github.com/Smolke9/Jenkins-Maven-Project.git`
- **Build Step**: Invoke top-level Maven targets
  - Maven Version: `mymaven`
  - Goals: `test`

✅ Result: Test results shown in console.

---


---

## ✅ Summary

| Task         | Tool     |
|--------------|----------|
| Build        | Jenkins Freestyle |
| Project Type | Java + Maven |
| SCM          | GitHub |
| CI Trigger   | GitHub Webhook |
| Maven Goals  | clean package, test |
