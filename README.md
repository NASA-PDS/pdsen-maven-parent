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
git commit -m "release v$VERSION"
```

2. Deploy to Sonatype (Maven Central)
```
# For operational release
mvn clean site deploy -P release

# For snapshot
mvn clean site deploy
```

3. Tag a release in Github and push changes to `main`
```
git tag v${VERSION} -m "[RELEASE] pdsen-maven-parent v$VERSION" -m "See [CHANGELOG](https://github.com/NASA-PDS/pdsen-maven-parent/blob/main/CHANGELOG.md) for more details."
git push --tags
git push origin main
```

4. Back to development version
```
VERSION=1.12.0-SNAPSHOT
mvn versions:set -DnewVersion=$VERSION
git add pom.xml
git commit -m "start development on $VERSION"
```
