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
