# Sample project for OWASP Dependency Check issue 1444
This project contains samples that demonstrate the issues reported in DC issue 1444
## issue1444-faulty
This folder contains  project that shows the reported faulty behaviour when DC plugin is configured as a reporting plugin.

Running `mvn site:site` on this project works as expected: a dependency-check report is creeated and the slf4j-api vulnerability in the project is suppressed.

But running `mvn dependency-check:aggregate` as reported, or `mvn dependency-check:check`: a dependency-check report is created containing a vulnerability for the slf4j-api library as the suppressionfile is not used:

<details><summary><em>mvn site:site</em> output</summary>

```text
[INFO] Scanning for projects...
[INFO] 
[INFO] -------------< org.owasp.dependencycheck:issue1444-faulty >-------------
[INFO] Building issue1444-faulty 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-site-plugin:3.7.1:site (default-cli) @ issue1444-faulty ---
[INFO] configuring report plugin org.owasp:dependency-check-maven:4.0.1
[INFO] 1 report detected for dependency-check-maven:4.0.1: check
[INFO] configuring report plugin org.apache.maven.plugins:maven-project-info-reports-plugin:2.9
[INFO] 15 reports detected for maven-project-info-reports-plugin:2.9: cim, dependencies, dependency-info, dependency-management, distribution-management, index, issue-tracking, license, mailing-list, modules, plugin-management, plugins, project-team, scm, summary
[INFO] Rendering site with default locale English (en)
[INFO] Relativizing decoration links with respect to localized project URL: http://maven.apache.org
[INFO] Rendering content with org.apache.maven.skins:maven-default-skin:jar:1.2 skin.
[INFO] Generating "dependency-check" report --- dependency-check-maven:4.0.1:check
[INFO] Central analyzer disabled
[INFO] Checking for updates
[INFO] Skipping NVD check since last check was within 4 hours.
[INFO] Skipping RetireJS update since last update was within 24 hours.
[INFO] Check for updates complete (49 ms)
[INFO] Analysis Started
[INFO] Finished Archive Analyzer (0 seconds)
[INFO] Finished File Name Analyzer (0 seconds)
[INFO] Finished Jar Analyzer (0 seconds)
[INFO] Finished Dependency Merging Analyzer (0 seconds)
[INFO] Finished Version Filter Analyzer (0 seconds)
[INFO] Finished Hint Analyzer (0 seconds)
[INFO] Created CPE Index (1 seconds)
[INFO] Skipping CPE Analysis for npm
[INFO] Finished CPE Analyzer (1 seconds)
[INFO] Finished False Positive Analyzer (0 seconds)
[INFO] Finished NVD CVE Analyzer (0 seconds)
[INFO] Finished Vulnerability Suppression Analyzer (0 seconds)
[INFO] Finished Dependency Bundling Analyzer (0 seconds)
[INFO] Analysis Complete (1 seconds)
[INFO] Generating "Dependencies" report  --- maven-project-info-reports-plugin:2.9:dependencies
[WARNING] The repository url 'https://nexus.aikebah.net/nexus/content/groups/public/' is invalid - Repository 'nexus' will be blacklisted.
[INFO] Generating "Dependency Information" report --- maven-project-info-reports-plugin:2.9:dependency-info
[INFO] Generating "About" report         --- maven-project-info-reports-plugin:2.9:index
[INFO] Generating "Plugin Management" report --- maven-project-info-reports-plugin:2.9:plugin-management
[INFO] Generating "Plugins" report       --- maven-project-info-reports-plugin:2.9:plugins
[INFO] Generating "Summary" report       --- maven-project-info-reports-plugin:2.9:summary
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  7.642 s
[INFO] Finished at: 2018-12-17T22:34:15+01:00
[INFO] ------------------------------------------------------------------------
[WARNING] The requested profile "jrebel" could not be activated because it does not exist.

Process finished with exit code 0
```

</details>

<details><summary><em>mvn dependency-check:aggregate</em> output</summary>

```text
[INFO] Scanning for projects...
[INFO] 
[INFO] -------------< org.owasp.dependencycheck:issue1444-faulty >-------------
[INFO] Building issue1444-faulty 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- dependency-check-maven:4.0.1:aggregate (default-cli) @ issue1444-faulty ---
[INFO] Central analyzer disabled
[INFO] Checking for updates
[INFO] Skipping NVD check since last check was within 4 hours.
[INFO] Skipping RetireJS update since last update was within 24 hours.
[INFO] Check for updates complete (48 ms)
[INFO] Analysis Started
[INFO] Finished Archive Analyzer (0 seconds)
[INFO] Finished File Name Analyzer (0 seconds)
[INFO] Finished Jar Analyzer (0 seconds)
[INFO] Finished Dependency Merging Analyzer (0 seconds)
[INFO] Finished Version Filter Analyzer (0 seconds)
[INFO] Finished Hint Analyzer (0 seconds)
[INFO] Created CPE Index (1 seconds)
[INFO] Skipping CPE Analysis for npm
[INFO] Finished CPE Analyzer (1 seconds)
[INFO] Finished False Positive Analyzer (0 seconds)
[INFO] Finished NVD CVE Analyzer (0 seconds)
[INFO] Finished Vulnerability Suppression Analyzer (0 seconds)
[INFO] Finished Dependency Bundling Analyzer (0 seconds)
[INFO] Analysis Complete (1 seconds)
[WARNING] 

One or more dependencies were identified with known vulnerabilities in issue1444-faulty:

slf4j-api-1.7.7.jar (cpe:/a:slf4j:slf4j:1.7.7, org.slf4j:slf4j-api:1.7.7) : CVE-2018-8088


See the dependency-check report for more details.


[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  5.398 s
[INFO] Finished at: 2018-12-17T22:37:03+01:00
[INFO] ------------------------------------------------------------------------
[WARNING] The requested profile "jrebel" could not be activated because it does not exist.

Process finished with exit code 0
```

</details>

<details><summary><em>mvn dependency-check:check</em> output</summary>

```text
[INFO] Scanning for projects...
[INFO] 
[INFO] -------------< org.owasp.dependencycheck:issue1444-faulty >-------------
[INFO] Building issue1444-faulty 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- dependency-check-maven:4.0.1:check (default-cli) @ issue1444-faulty ---
[INFO] Central analyzer disabled
[INFO] Checking for updates
[INFO] Skipping NVD check since last check was within 4 hours.
[INFO] Skipping RetireJS update since last update was within 24 hours.
[INFO] Check for updates complete (52 ms)
[INFO] Analysis Started
[INFO] Finished Archive Analyzer (0 seconds)
[INFO] Finished File Name Analyzer (0 seconds)
[INFO] Finished Jar Analyzer (0 seconds)
[INFO] Finished Dependency Merging Analyzer (0 seconds)
[INFO] Finished Version Filter Analyzer (0 seconds)
[INFO] Finished Hint Analyzer (0 seconds)
[INFO] Created CPE Index (1 seconds)
[INFO] Skipping CPE Analysis for npm
[INFO] Finished CPE Analyzer (1 seconds)
[INFO] Finished False Positive Analyzer (0 seconds)
[INFO] Finished NVD CVE Analyzer (0 seconds)
[INFO] Finished Vulnerability Suppression Analyzer (0 seconds)
[INFO] Finished Dependency Bundling Analyzer (0 seconds)
[INFO] Analysis Complete (1 seconds)
[WARNING] 

One or more dependencies were identified with known vulnerabilities in issue1444-faulty:

slf4j-api-1.7.7.jar (cpe:/a:slf4j:slf4j:1.7.7, org.slf4j:slf4j-api:1.7.7) : CVE-2018-8088


See the dependency-check report for more details.


[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  5.416 s
[INFO] Finished at: 2018-12-17T22:34:52+01:00
[INFO] ------------------------------------------------------------------------
[WARNING] The requested profile "jrebel" could not be activated because it does not exist.

Process finished with exit code 0
```
</details>

## issue1444-working
This folder contains  project that shows the reported working behaviour when DC plugin is configured as a build plugin.

Running either `mvn dependency-check:check` or `mvn dependency-check:aggregate` on this project works as expected: a dependency-check report is created and the slf4j-api vulnerability in the project is suppressed. As dependency-check is not configured as a reporting-plugin running `mvn site:site` does not trigger dependency-check execution.


<details><summary><em>mvn site:site</em> output</summary>

```text
[INFO] Scanning for projects...
[INFO] 
[INFO] ------------< org.owasp.dependencycheck:issue1444-working >-------------
[INFO] Building issue1444-working 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-site-plugin:3.7.1:site (default-cli) @ issue1444-working ---
[INFO] configuring report plugin org.apache.maven.plugins:maven-project-info-reports-plugin:2.9
[INFO] 15 reports detected for maven-project-info-reports-plugin:2.9: cim, dependencies, dependency-info, dependency-management, distribution-management, index, issue-tracking, license, mailing-list, modules, plugin-management, plugins, project-team, scm, summary
[INFO] Rendering site with default locale English (en)
[INFO] Relativizing decoration links with respect to localized project URL: http://maven.apache.org
[INFO] Rendering content with org.apache.maven.skins:maven-default-skin:jar:1.2 skin.
[INFO] Generating "Dependencies" report  --- maven-project-info-reports-plugin:2.9:dependencies
[WARNING] The repository url 'https://nexus.aikebah.net/nexus/content/groups/public/' is invalid - Repository 'nexus' will be blacklisted.
[INFO] Generating "Dependency Information" report --- maven-project-info-reports-plugin:2.9:dependency-info
[INFO] Generating "About" report         --- maven-project-info-reports-plugin:2.9:index
[INFO] Generating "Plugin Management" report --- maven-project-info-reports-plugin:2.9:plugin-management
[INFO] Generating "Plugins" report       --- maven-project-info-reports-plugin:2.9:plugins
[INFO] Generating "Summary" report       --- maven-project-info-reports-plugin:2.9:summary
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  3.211 s
[INFO] Finished at: 2018-12-17T23:03:00+01:00
[INFO] ------------------------------------------------------------------------
[WARNING] The requested profile "jrebel" could not be activated because it does not exist.

Process finished with exit code 0
```
</details>

<details><summary><em>mvn dependency-check:aggregate</em> output</summary>

```text
[INFO] Scanning for projects...
[INFO] 
[INFO] ------------< org.owasp.dependencycheck:issue1444-working >-------------
[INFO] Building issue1444-working 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- dependency-check-maven:4.0.1:aggregate (default-cli) @ issue1444-working ---
[INFO] Central analyzer disabled
[INFO] Checking for updates
[INFO] Skipping NVD check since last check was within 4 hours.
[INFO] Skipping RetireJS update since last update was within 24 hours.
[INFO] Check for updates complete (53 ms)
[INFO] Analysis Started
[INFO] Finished Archive Analyzer (0 seconds)
[INFO] Finished File Name Analyzer (0 seconds)
[INFO] Finished Jar Analyzer (0 seconds)
[INFO] Finished Dependency Merging Analyzer (0 seconds)
[INFO] Finished Version Filter Analyzer (0 seconds)
[INFO] Finished Hint Analyzer (0 seconds)
[INFO] Created CPE Index (1 seconds)
[INFO] Skipping CPE Analysis for npm
[INFO] Finished CPE Analyzer (1 seconds)
[INFO] Finished False Positive Analyzer (0 seconds)
[INFO] Finished NVD CVE Analyzer (0 seconds)
[INFO] Finished Vulnerability Suppression Analyzer (0 seconds)
[INFO] Finished Dependency Bundling Analyzer (0 seconds)
[INFO] Analysis Complete (1 seconds)
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  5.360 s
[INFO] Finished at: 2018-12-17T23:04:43+01:00
[INFO] ------------------------------------------------------------------------
[WARNING] The requested profile "jrebel" could not be activated because it does not exist.

Process finished with exit code 0
```
</details>

<details><summary><em>mvn dependency-check:check</em> output</summary>

```text
[INFO] Scanning for projects...
[INFO] 
[INFO] ------------< org.owasp.dependencycheck:issue1444-working >-------------
[INFO] Building issue1444-working 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- dependency-check-maven:4.0.1:check (default-cli) @ issue1444-working ---
[INFO] Central analyzer disabled
[INFO] Checking for updates
[INFO] Skipping NVD check since last check was within 4 hours.
[INFO] Skipping RetireJS update since last update was within 24 hours.
[INFO] Check for updates complete (48 ms)
[INFO] Analysis Started
[INFO] Finished Archive Analyzer (0 seconds)
[INFO] Finished File Name Analyzer (0 seconds)
[INFO] Finished Jar Analyzer (0 seconds)
[INFO] Finished Dependency Merging Analyzer (0 seconds)
[INFO] Finished Version Filter Analyzer (0 seconds)
[INFO] Finished Hint Analyzer (0 seconds)
[INFO] Created CPE Index (1 seconds)
[INFO] Skipping CPE Analysis for npm
[INFO] Finished CPE Analyzer (1 seconds)
[INFO] Finished False Positive Analyzer (0 seconds)
[INFO] Finished NVD CVE Analyzer (0 seconds)
[INFO] Finished Vulnerability Suppression Analyzer (0 seconds)
[INFO] Finished Dependency Bundling Analyzer (0 seconds)
[INFO] Analysis Complete (1 seconds)
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  5.468 s
[INFO] Finished at: 2018-12-17T23:05:26+01:00
[INFO] ------------------------------------------------------------------------
[WARNING] The requested profile "jrebel" could not be activated because it does not exist.

Process finished with exit code 0
```
</details>

