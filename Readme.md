# ⚙️ DevOps Lab – Azure Pipeline with Self-Hosted Agent

> CI pipeline using Azure DevOps with a self-hosted agent that builds and tests a Java project using Apache Maven.

![Azure DevOps](https://img.shields.io/badge/Azure-DevOps-blue.svg)
![Java](https://img.shields.io/badge/Java-JDK-orange.svg)
![Maven](https://img.shields.io/badge/Apache-Maven-red.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Status](https://img.shields.io/badge/status-Complete-brightgreen.svg)

---

## Overview

This project demonstrates how to create and run a CI pipeline using Azure DevOps with a self-hosted agent. The pipeline builds and tests a simple Java project using Apache Maven.

The main goal of this experiment is to understand:

- Azure DevOps Pipelines
- Self-Hosted Agents
- Personal Access Token (PAT) authentication
- Maven build and test execution
- Continuous Integration (CI)

---

## Technologies Used

| Technology | Purpose |
|---|---|
| Azure DevOps | CI/CD Platform |
| GitHub | Source Code Repository |
| Apache Maven | Build & Dependency Management |
| Java (JDK) | Programming Language |
| JUnit | Testing Framework |
| Self-Hosted Agent | Pipeline Execution |
| Windows OS | Agent Host Machine |

---

## Repository Structure
```
DevOps-Lab/
│
├── pom.xml
├── azure-pipelines.yml
└── src/
    └── test/
        └── java/
            └── SampleTest.java
```

---

## Pipeline Workflow

The Azure pipeline contains two stages:

### 1. Build Stage
Compiles the Java project using Maven.
```bash
mvn clean compile
```

### 2. Test Stage
Runs regression test cases using Maven.
```bash
mvn test
```

> The Test stage depends on the Build stage — tests will only run if the build succeeds.

---

## Steps Performed

### 1. Create GitHub Repository
A repository named `DevOps-Lab` was created and connected to Azure DevOps.

### 2. Generate Personal Access Token (PAT)
A PAT was created in Azure DevOps to authenticate the agent with the organization.

### 3. Configure Self-Hosted Agent
The Azure DevOps agent was downloaded and configured on the local machine.

Agent configuration included:
- Server URL
- Personal Access Token
- Agent Pool (Default)
- Agent Name (`local-agent`)

The agent was installed as a **Windows Service** so it runs automatically.

### 4. Install Required Tools

**Java**
Java Development Kit (JDK) was installed on the host machine.

**Maven**
Apache Maven was installed and configured using environment variables:
- `MAVEN_HOME`
- Updated `PATH`

Verification:
```bash
mvn -v
```

### 5. Create Maven Project Configuration
A `pom.xml` file was created to define project dependencies and build configuration. JUnit dependency was added to support testing.

### 6. Create Test Case
A simple test class `SampleTest.java` was created.
```java
assertTrue(true);
```

This confirms the pipeline can successfully discover and run test cases.

### 7. Create Azure Pipeline
A pipeline configuration file `azure-pipelines.yml` was created in the repository.

The pipeline:
- Triggers on commits to the `main` branch
- Uses the self-hosted agent pool
- Executes build and test stages sequentially

---

## Running the Pipeline

Once the agent is online, trigger the pipeline by either:

1. Pushing code to the `main` branch, or
2. Manually running the pipeline from Azure DevOps

The pipeline will automatically:
1. Compile the project
2. Run regression tests

---

## Key Concepts Learned

- Continuous Integration (CI)
- Azure DevOps Pipelines
- Self-Hosted Agent configuration
- Maven build lifecycle
- Regression testing
- Automated testing in CI/CD pipelines

---

## Conclusion

This experiment demonstrates how a self-hosted Azure DevOps pipeline can be used to automate the build and testing process of a Java project using Maven. The setup allows developers to continuously integrate code changes and verify functionality through automated regression tests.

---
