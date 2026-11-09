# open-source-parent
The Open Source parent of all TOPdesk Open Source projects.

# Releasing
Releases are published to Maven Central by the `Release to Maven Central` GitHub Actions workflow.

1. Add the new version to the changelog below and merge it to `main`.
2. Create a GitHub release whose tag is the version (e.g. `5.0.0` or `v5.0.0`).

The workflow sets that version in the pom, builds, signs and publishes it with `mvn deploy -Psonatype-oss-release`. It can also be started manually from the *Actions* tab. It needs these repository secrets: `MAVEN_CENTRAL_USERNAME` and `MAVEN_CENTRAL_PASSWORD` (Central Portal token), `MAVEN_GPG_PRIVATE_KEY` and `MAVEN_GPG_PASSPHRASE`.

Child projects publish the same way by activating the `sonatype-oss-release` profile.

# Changelog
**5.0.0**

* Change default `java.version` from 21 to 25
* Publish to Maven Central through the Central Portal (`central-publishing-maven-plugin`) instead of the retired OSSRH (`oss.sonatype.org`)
* The `sonatype-oss-release` profile now also publishes (`mvn deploy -Psonatype-oss-release`); it needs a `central` server (user token) in `settings.xml`

**4.0.0**

* Change default `java.version` from 17 to 21
* Updated plugins and dependencies

**3.1.0**

* Updated plugins and dependencies

**3.0.0**

* Change default `java.version` from 11 to 17
* Updated plugins and dependencies

**2.0.1**

* Added the java.version as release in the compiler plugin

**2.0.0**

* Updated plugins
* Change default `java.version` from 8 to 11

**1.2.0**

* Updated plugins
* Change default `java.version` from 1.8 to 8

**1.1.0**

* Updated plugins and dependencies
* Follow Maven 3.5 best practices: use the maven-enforcer-plugin to specify the minimum required Maven version

**1.0.0**

* Initial release

# Releasing

Execute: `mvn release:prepare release:perform -P sonatype-oss-release`