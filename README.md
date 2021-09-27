# PDS Engineering Node Maven Parent POM

This project is simply the parent [project object model (POM)](https://maven.apache.org/pom.html) for [Planetary Data System](https://pds.nasa.gov/) projects using [Apache Maven](https://maven.apache.org/) or compatible project management tools. It includes some common repositories, distribution management, plugins, and reporting information all `gov.nasa.pds` projects inherit and take advantage of.

See [pom.xml](https://github.com/nasa-pds/pdsen-maven-parent/blob/main/pom.xml) for more information.


## Getting Started

To configure your project to use the PDS Maven Parent, add the `<parent>` designation to your own POM:
```xml
<parent>
    <groupId>gov.nasa</groupId>
    <artifactId>pds</artifactId>
    <version>{VERSION}</version>
</parent>
```
To get the latest version, see what has been deployed to the [Maven Central Repository](https://search.maven.org/artifact/gov.nasa/pds).


## 👥 Contributing

Within the NASA Planetary Data System, we value the health of our community as much as the code. Towards that end, we ask that you read and practice what's described in these documents:

-   Our [contributor's guide](https://github.com/NASA-PDS/.github/blob/main/CONTRIBUTING.md) delineates the kinds of contributions we accept.
-   Our [code of conduct](https://github.com/NASA-PDS/.github/blob/main/CODE_OF_CONDUCT.md) outlines the standards of behavior we practice and expect by everyone who participates with our software.


## Release and Deployment

This [repository on GitHub](https://github.com/NASA-PDS/pdsen-maven-parent) takes advantage of [GitHub Actions](https://github.com/features/actions) to perform routine, automatic deployment of the parent POM. The instructions that follow below remain in order to describe how to do a release manually.

In the event updates are made to the POM and they are ready for release, perform the following steps:

1. Version the POM to a new version.
```console
$ VERSION=1.1.0
$ mvn versions:set -DnewVersion=$VERSION
$ git add pom.xml
$ git commit -m "release v$VERSION"
```

2. Deploy to Sonatype (Maven Central).
```console
$ # For operational release
$ mvn clean site deploy -P release
$
$ # For snapshot
$ mvn clean site deploy
```

3. Tag a release in Github and push changes to `main`
```console
$ git tag v${VERSION} -m "[RELEASE] pdsen-maven-parent v$VERSION" -m "See [CHANGELOG](https://github.com/NASA-PDS/pdsen-maven-parent/blob/main/CHANGELOG.md) for more details."
$ git push --tags
$ git push origin main
```

4. Back to development version
```console
$ VERSION=1.12.0-SNAPSHOT
$ mvn versions:set -DnewVersion=$VERSION
$ git add pom.xml
$ git commit -m "start development on $VERSION"
```


## 📃 License

The project is licensed under the [Apache version 2](LICENSE.md) license. Or it isn't. Change this after consulting with your lawyers.

