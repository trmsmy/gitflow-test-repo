# Gitflow maven plugin test repository 

It's a maven sample project to test out the following gitlflow plugins

* https://github.com/egineering-llc/gitflow-helper-maven-plugin
* https://github.com/aleksandr-m/gitflow-maven-plugin 

The pom.xml is configured with these plugins. 

## gitflow-maven plugin 

### Configuration 

```xml

<plugin>
    <groupId>com.amashchenko.maven.plugin</groupId>
    <artifactId>gitflow-maven-plugin</artifactId>
    <version>1.9.0</version>
    <configuration>
        <commitMessages>
            <featureStartMessage>Start feature, featureName: @{featureName}</featureStartMessage>
            <featureFinishMessage>Finished feature and merging to development branch, featureName:@{featureName}</featureFinishMessage>

            <hotfixStartMessage>Start hotfix @{version}</hotfixStartMessage>
            <hotfixFinishMessage>Finished hotfix @{version}</hotfixFinishMessage>

            <releaseStartMessage>Start release branch, version @{version}</releaseStartMessage>
            <releaseFinishMessage>Finish relase branch, version @{version}</releaseFinishMessage>

            <tagHotfixMessage>tag hotfix - @{version}</tagHotfixMessage>
            <tagReleaseMessage>tag release - @{version}</tagReleaseMessage>
        </commitMessages>
    </configuration>
</plugin>

```

## gitflow-helper maven plugin 

### Configuration 

```xml 

<plugin>
    <groupId>com.e-gineering</groupId>
    <artifactId>gitflow-helper-maven-plugin</artifactId>
    <version>1.7.2</version>
    <extensions>true</extensions>

    <configuration>
        <releaseDeploymentRepository>local-nexus::default::http://localhost:9999/nexus/content/repositories/releases::false</releaseDeploymentRepository>
        <stageDeploymentRepository>local-nexus::default::http://localhost:9999/nexus/content/repositories/staging::false</stageDeploymentRepository>
        <snapshotDeploymentRepository>local-nexus::default::http://localhost:9999/nexus/content/repositories/snapshots::true</snapshotDeploymentRepository>
    </configuration>
    <executions>
        <execution>
            
                <goals>
                    <!-- <goal>enforce-versions</goal> -->
                    <goal>retarget-deploy</goal>
                    <goal>update-stage-dependencies</goal>
                    <!-- <goal>set-properties</goal> -->
                    <goal>promote-master</goal>
                </goals>
            
        </execution>
    </executions>
 </plugin>  

```

The project needs access to Nexus repository with 3 repos 

* snapshot 
* staging 
* releases 

The configuration for nexus is included in the gitflow-helper plugin's configuration 