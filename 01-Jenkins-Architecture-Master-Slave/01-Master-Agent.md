# 01. Understanding Jenkins Architecture: Master vs. Agent Key Concept:
      - Jenkins follows a distributed, master-agent architecture to efficiently manage and execute build pipelines. 
        The Master (or Controller) orchestrates the process, while one or more Agents (or nodes) perform the actual work.


# 02. What Is the Jenkins Master?
      - Definition: The Master is the central Jenkins Server often called the Controller, that provides the web interface, store
        configuration, schedules jobs, and manages agents.
      
      - Core Responsibilities:
        a. Job Scheduling & Coordination: Determines when and where each build or pipeline should run.

        b. Configuration Management: Maintains global settings, job definitions, credentials, and plugin installations.

        c. User Interface: Hosts the web UI where users create jobs, view build results, and configure Jenkins.

        d. Monitoring & Reporting: Tracks agent availability, collects build results, and displays logs and metrics.

        e. Access Control: Authenticates users and enforces roles/permissions.

      - Real-World Analogy: Imagine a restaurant kitchen manager (Master) who:
        a. Receives orders (code commits).
        b. Assigns each dish (build task) to available chefs (Agents).
        c. Tracks order progress.
        d. Communicates status to waitstaff and customers (developers).


# 03. What Is a Jenkins Agent?
      - Definition: An Agent (formerly known as “slave”) is a worker machine—physical, virtual, container, or cloud instance—that connects to the 
        Master and runs build tasks.
      
      - Core Responsibilities:
        a. Task Execution: Performs the steps defined in a job, such as compiling code, running tests, or deploying artifacts.

        b. Multiple Executors: Each Agent can support several executors, enabling parallel job execution.

        c. Environment Isolation: Agents can be configured with different OS, tools, and libraries for specific tasks.

        d. Result Reporting: Sends build status, logs, and artifacts back to the Master.

      - Types of Agents:
        a. Permanent Agents: Always connected to Jenkins, ideal for recurring workloads.

        b. Ephemeral Agents: Dynamically provisioned (e.g., via Docker or cloud), spun up for individual builds, then terminated.

      - Real-World Analogy: Think of chefs in the kitchen:
        a. Each chef (Agent) specializes in certain cuisines (environments).
        b. When the manager (Master) assigns a dish (build), the chef prepares it.
        c. Upon completion, the chef notifies the manager of the dish’s readiness (build success/failure).


# 04. How Master and Agents Communicate
      a. Protocols Used:
         - SSH or Java Network Launch Protocol (JNLP) over TCP/IP.
      
      b. Connection Flow:
         - Agents initiate a connection to the Master (or vice versa), establishing a secure channel.
         - Master dispatches build tasks to Agents via this channel.
         - Agents stream logs and results back to the Master in real time.
      
      c. Labeling & Assignment:
         - Agents are tagged with labels (e.g., linux, windows, docker).
         - Jobs specify required labels to ensure they run on compatible Agents.


# 05. Simple Workflow Example
      a. A developer pushes code to GitHub.
      b. Jenkins Master detects the change and schedules a job.
      c. Master selects an appropriate Agent (e.g., labeled linux).
      d. Agent checks out the code, runs build and tests.
      e. Agent streams logs back; on completion, sends status and artifacts.
      f. Master updates the UI and notifies the team via email or Slack.


