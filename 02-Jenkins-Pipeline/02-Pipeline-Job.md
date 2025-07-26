# 01. What is a Pipeline Job?

- A pipeline job defines your entire build process as code using a **Jenkinsfile** written in a **Groovy-based Domain specific Language (DSL)**


# 02. Real-World Anal chain operations director writing a comprehensive operations manual:

```
restaurantOperations {
    parallel {
        kitchenPrep: ["check inventory", "prep ingredients"]
        diningSetup: ["clean tables", "set silverware"]  
    }
    sequential {
        serviceHours: ["serve customers", "handle orders"]
        cleanup: ["clean kitchen", "balance register"]
    }
    notifications: ["send daily report", "alert management"]
}
```

- This manual is stored in your company's version control system, can be reviewed by other managers, and if operations are interrupted, you can 
  resume exactly where you left off


# 03. Key Characteristics:

- **a. Code-Based:** Entire pipeline defined in a Jenkinsfile
- **b. Version Controlled:** Pipeline stored with your source code.
- **c. Durable:** Can survive and resume after Jenkins restarts.
- **d. Advanced Features:** Supports parallel execution, stages, conditional logic


# 04. Use Pipeline Jobs When:

- **a. Complex Workflows:** Multi-stage, conditional, or parallel processes.
- **b. Version Control:** Need to track changes to build process.
- **c. Team Collaboration:** Multiple developers working on build process.
- **d. Scalability:** Managing multiple similar projects.
- **e. Modern DevOps:** Implementing Pipeline-as-Code practices.