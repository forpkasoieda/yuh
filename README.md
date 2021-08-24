# Android Sonarcloud Sample Project

Set environment variables in your codemagic.yaml:

```
SONAR_TOKEN: Encrypted(...)
SONAR_PROJECT_KEY: Encrypted(...)
SONAR_ORG_KEY: Encrypted(...)
```

These values are available in your Sonarcloud account and can be encrypted in the Codemagic web app.

Add the sonarqube plugin to app/build.gradle
```
plugins {
    ...
    id "org.sonarqube" version "3.3"
    ...
}
```

Set the Sonarqube properties in app/build.gradle. Change the branch as required or also set that as an environment variable.

```
sonarqube {
    properties {
        property "sonar.branch", "gradle-config"
        property "sonar.host.url", "https://sonarcloud.io"
        property "sonar.projectKey", System.getenv("SONAR_PROJECT_KEY")
        property "sonar.organization", System.getenv("SONAR_ORG_KEY")
        property "sonar.branch.name", System.getenv("FCI_BRANCH")
        property "sonar.branch.target", System.getenv("FCI_PULL_REQUEST_DEST")
        property "sonar.login", System.getenv("SONAR_TOKEN")
    }
}
```
