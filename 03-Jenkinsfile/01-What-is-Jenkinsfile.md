# 01. What Is a Jenkinsfile and Pipeline-as-Code?
      - A Jenkinsfile is a text file that lives in your source repository and defines your entire CI/CD workflow, this approach is also
        known as Pipeline-as-Code.
      
      - Treating Pipelines-as-Code brings version control, collaboration, and automation best practices to your build, test, and deployment
        process.


# 02. Definition of a Jenkinsfile
      - A Jenkinsfile is a plain-text, Groovy-based configuration file that describes a Jenkins Pipeline, the sequence of steps Jenkins
        executes to build, test and deliver software.

      - Because it lives alongside your application source code, every change to your pipeline is automatically tracked, reviewed, and
        reproducible.
      
      - Pipeline-as-Code means you define job processes in a file (Jenkinsfile) stored and versioned in your repository rather than 
        manually clicking options in the Jenkins UI.
      
      - When Jenkins detects a Jenkinsfile in your project, it automatically creates and runs the pipeline, eliminating manual job
        setup and configuration drift.


# 03. Core Benefits of Pipeline-as-Code
      a. Version Control and Traceability
         - Every pipeline change is committed, diffed, and rollback-able just like application code.
      
      b. Collaboration and Review
         - Teams can peer-review changes to their CI/CD logic via pull requests.
      
      c. Consistency and Repeatability
         - The same Jenkinsfile can be resused across branches or repositories, esuring uniform build behaviour.
      
      d. Automation and Scalability
         - Jenkins can automatically discover and run pipelines for new branches or pull requests using Multibranch Pipelines
           or Organization Folders.


# 04. Real-World Analogy
      - Imagine you run a bakery:
        a. Previously, each baker wrote down their own recipe on sticky notes (manual UI jobs).
        b. Now, you keep every recipe in a shared recipe book (Jenkinsfile in Git).
        c. When a new order arrives, the kitchen manager (Jenkins) reads the recipe, assigns tasks to bakers (agents), and ensures each step mix, 
           proof, bake, box is executed exactly the same way every time.
      
      - This recipe book is your source of truth, reviewed by your team and versioned with every improvement.


# 05. Simple Jenkinsfile Example

```
pipeline {                                  // 1. Declare the pipeline
    agent any                               // 2. Run on any available worker

    stages {                                // 3. Define sequential stages
        stage('Build) {
            steps {
                echo 'Building'             // 4. Commands to execute
            }
        }

        stage('Test') {
            steps {
                echo 'Testing'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }

    post {                                  // 5. Actions after all stages
        success {
            echo 'Pipeline Succeeded'
        }
        failure {
            echo 'Pipeline Failed'
        }
    }
}
```

- **a. pipeline { … }:** Wraps the entire workflow.
- **agent any:** Uses any free build agent.
- **stages { … }:** Groups major phases (Build, Test, Deploy).
- **steps { … }:** Lists the actual commands run in each phase.
- **post { … }:** Defines notifications or cleanup after the run



# 06. How Jenkins Uses the Jenkinsfile
      
      a. When you Create Multibranch Pipeline job pointing at your repository, Jenkins scans for a file named Jenkinsfile in each branch

      b. Upon detecting it, Jenkins automatically provisions agents, checks out the code, and executes the defined stages without any
         manual configuration in the UI.
      
      c. If you add a new feature branch, Jenkins runs its pipeline too, instant CI for every branch.