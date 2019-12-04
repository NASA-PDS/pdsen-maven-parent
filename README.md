# PDS Engineering Node Maven Parent POM

# Description

This project is simply the parent POM for gov.nasa.pds projects using Maven. It includes 
some common repositories, distributionManagement, plugins, and reporting information all
gov.nasa.pds projects should inherit.

See [pom.xml](https://github.com/nasa-pds/pdsen-maven-parent/blob/master/pom.xml) for more information

# Release and Deployment

In the event updates are made to the POM and they are ready for release, perform the following steps:

1. Version the POM to a new version.

```
VERSION=1.1.0
mvn versions:set -DnewVersion=$VERSION
git add pom.xml
```

2. Deploy to Sonatype (Maven Central)
```
# For operational release
mvn clean site deploy -P release

# For release candidate
mvn clean site deploy
```

3. Tag a release in Github
```
git tag v${VERSION}
git push --tags
```