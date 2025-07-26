# 01. Declarative vs. Scripted Pipeline Syntax in Jenkins MAIN TAKEWAY
      - Jenkins offers 2 ways to write pipelines in a Jenkinsfile: 
        a. Declarative: A structured openionated syntax and
        b. Scripted: a free-form, programmatic Groovy Syntax.
      
      - Declarative pipelines  guide you with a clear template, while Scripted pipelines give you maximum flexibilty.


# 02. What Is a Declarative Pipeline?
      - A Declarative pipeline uses a predefined, easy-to-read structure. It enforces a pipeline {...} block, a fixed set of sections
        (agent, stages, post etc) and built-in validation.


# 03. Real-World Analogy:
      - Think of ordering at a fast-food restaurant with a menu form: you choose “Burger,” “Fries,” and “Drink” from fixed fields. The form ensures 
        you fill required sections in the right order.


# 04. Key Characteristics
      a. Structured Template: Always starts with pipeline {}.
      b. Built-in Blocks: Requires named sections—agent, environment, options, stages, post.
      c. Validation: Jenkins checks syntax before running.
      d. Readability: Ideal for beginners and teams to standardize pipelines.


# 05. Declarative Syntax Example

``` 
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building…'
      }
    }
    stage('Test') {
      steps {
        echo 'Testing…'
      }
    }
  }
  post {
    success { echo 'Done!' }
    failure { echo 'Oops!' }
  }
}
```

# 06. What Is a Scripted Pipeline?
      - A Scripted Pipeline is written as Groovy code inside a node {...} block. It offers full control over flow, conditions, loops, and
        custom logic.


# 07. Real-World Analogy:
      - Imagine you’re cooking in your own kitchen without a recipe form—free to add ingredients, loops (stir every 10 minutes), or conditional 
        steps (“if sauce is too thick, add water”). You control every detail.


# 08. Key Characteristics
      a. Code-First: Uses native Groovy.
      b. Flexible Flow: You can write loops, conditionals, and complex logic anywhere.
      c. No Enforced Structure: You choose how to organize node, stage, and custom functions.
      d. Advanced Use Cases: Best for dynamic pipelines or when you need programmatic control.


# 09. Scripted Syntax Example

```
node {
  try {
    stage('Build') {
      echo 'Building…'
    }
    stage('Test') {
      echo 'Testing…'
      if (env.BRANCH_NAME == 'main') {
        echo 'Running extra checks on main branch'
      }
    }
  } catch (err) {
    currentBuild.result = 'FAILURE'
    throw err
  } finally {
    stage('Cleanup') {
      echo 'Cleaning up workspace'
      cleanWs()
    }
  }
}
```


# 10. Which Should You Use?
      a. Start with Declarative if you’re new to Jenkins or want consistency across teams.

      b. Migrate to Scripted when you encounter limitations—such as dynamic parallelism, complex loops, or custom error handling.





