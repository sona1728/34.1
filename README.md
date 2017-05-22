Ques: Explain in brief:
● The complete structure and the working of “Oozie Workflow scheduler “
Ans:
# Structure of oozie:
- Apache Oozie is an open source project based on Java™ technology that simplifies the process of creating workflows and managing coordination among jobs.

- In principle, Oozie offers the ability to combine multiple jobs sequentially into one logical unit of work. One advantage of the Oozie framework is that it is fully integrated with the Apache Hadoop stack and supports Hadoop jobs for Apache MapReduce, Pig, Hive, and Sqoop.

- In addition, it can be used to schedule jobs specific to a system, such as Java programs. Therefore, using Oozie, Hadoop administrators are able to build complex data transformations that can combine the processing of different individual tasks and even sub-workflows. This ability allows for greater control over complex jobs and makes it easier to repeat those jobs at predetermined periods.

*In practice, there are different types of Oozie jobs:

> Oozie Workflow jobs — Represented as directed acyclical graphs to specify a sequence of actions to be executed.
> Oozie Coordinator jobs — Represent Oozie workflow jobs triggered by time and data availability.
> Oozie Bundle— Facilitates packaging multiple coordinator and workflow jobs, and makes it easier to manage the life cycle of those jobs.

# Working of “Oozie Workflow scheduler “:

- An Oozie workflow is a collection of actions arranged in a directed acyclic graph (DAG). 
- This graph can contain two types of nodes: control nodes and action nodes. 
- Control nodes, which are used to define job chronology, provide the rules for beginning and ending a workflow and control the workflow execution path with possible decision points known as fork and join nodes. 
- Action nodes are used to trigger the execution of tasks. 
- In particular, an action node can be a MapReduce job, a Pig application, a file system task, or a Java application. (The shell and ssh actions have been deprecated).

 Oozie is a native Hadoop stack integration that supports all types of Hadoop jobs and is integrated with the Hadoop stack.
 - In particular, Oozie is responsible for triggering the workflow actions, while the actual execution of the tasks is done using Hadoop MapReduce. Therefore, Oozie becomes able to leverage existing Hadoop machinery for load balancing, fail-over, etc.
 - Oozie detects completion of tasks through callback and polling. When Oozie starts a task, it provides a unique callback HTTP URL to the task, and notifies that URL when it is complete.
 - If the task fails to invoke the callback URL, Oozie can poll the task for completion. Figure 1 illustrates a sample Oozie workflow that combines six action nodes (Pig scrip, MapReduce jobs, Java code, and HDFS task) and five control nodes (Start, Decision control, Fork, Join, and End). 
 - Oozie workflows can be also parameterized. When submitting a workflow job, values for the parameters must be provided. If the appropriate parameters are used, several identical workflow jobs can occur concurrently.
