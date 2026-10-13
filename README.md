# Course Registration

This is a Java project built using Maven and JUnit 5.

## Project Structure

- pom.xml – Parent POM with shared settings and dependencies.
- course-registration-app/ – Contains the application code, tests, and child POM.

## Build and Test

Run these commands from the project root:

```bash
mvn clean test
mvn package
```

The tests use JUnit 5. Test reports and the packaged JAR are available in course-registration-app/target/ folder

So far the last test run passed all 10 tests with no failures or errors.



## Jenkins Pipeline Explanation (Jenkinsfile)

    Execution: Runs mvn clean test and mvn package from the repository root using Windows bat steps.

    Reporting & Safety: Automatically publishes JUnit XML reports from course-registration-app/target/surefire-reports/. If tests fail, the pipeline aborts, preventing artifact packaging and archiving.


### d) How the Deployment Controller Maintains Replicas

The Deployment Controller runs as part of the Kubernetes control plane inside the kube-controller-manager. It continuously monitors the state of the cluster through the API server, comparing the current state (actual number of running Pods matching the selector app=nginx) with the desired state (spec.replicas: 3).

During Scaling: When you change the replica count from 2 to 3, the controller detects the deficit (2 actual vs. 3 desired) and instructs the scheduler to create a new Pod.

During Self-Healing: When you delete a Pod, the actual count drops to 2. The controller immediately notices this discrepancy, recognizes that the desired count is 3, and automatically triggers the creation of a brand new replacement Pod with the same configuration to restore the desired state.