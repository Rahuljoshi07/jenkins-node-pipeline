# 🧪 Node.js CI Pipeline with Jenkins

A simple and professional example of setting up a **Continuous Integration (CI)** pipeline using **Jenkins** and **Node.js**. This project showcases automated dependency installation, test execution, and build feedback using a declarative Jenkins Pipeline.

---

## 📂 Project Structure

```
jenkins-node-pipeline/
├── index.js         # Core logic (add function)
├── test.js          # Unit test file
├── package.json     # Project metadata & npm scripts
└── Jenkinsfile      # Jenkins pipeline configuration
```

---

## 📌 Features

- ✅ Automated CI pipeline using Jenkins
- 📦 Installs dependencies with `npm install`
- 🔍 Runs unit tests via `npm test`
- ☁️ Integrates seamlessly with GitHub
- ⚙️ Uses Node.js 24 (managed in Jenkins)

---

## 🛠️ Setup Instructions

### 1. Prerequisites

- Node.js plugin installed in Jenkins
- Jenkins with pipeline and Git support
- Node.js (e.g., `Node_24`) added under **Manage Jenkins → Global Tool Configuration**
- GitHub repository with the project code

---

### 2. Jenkinsfile

```groovy
pipeline {
  agent any

  tools {
    nodejs 'Node_24' // Must match your tool name in Jenkins
  }

  stages {
    stage('Install') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
  }
}
```

---

## 💻 Code Overview

### `index.js`

```js
function add(a, b) {
  return a + b;
}
module.exports = add;
```

### `test.js`

```js
const add = require('./index');

const testCases = [
  { a: 1, b: 2, expected: 3 },
  { a: 5, b: 7, expected: 12 },
  { a: -1, b: 1, expected: 0 },
];

for (const { a, b, expected } of testCases) {
  const result = add(a, b);
  if (result !== expected) {
    console.error(`❌ Test failed: add(${a}, ${b}) = ${result}, expected ${expected}`);
    process.exit(1);
  }
}
console.log("✅ All tests passed!");
```

---

### `package.json`

```json
{
  "name": "jenkins-node-pipeline",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "node test.js"
  },
  "author": "Rahul Joshi",
  "license": "ISC"
}
```

---

## 📸 CI Pipeline Demo

When this repository is connected to a Jenkins project:

- Jenkins checks out the Git repo.
- Installs Node.js 24 via the configured tool.
- Runs `npm install` and `npm test`.
- Pipeline marks build as ✅ **Success** if all tests pass, ❌ **Failure** otherwise.

---

## 🙋‍♂️ Author

**Rahul Joshi**  
DevOps & Cloud Enthusiast | Game Dev Hobbyist  
📫 [GitHub](https://github.com/Rahuljoshi07)

---

## 📄 License

Free to use and modify.
