# Templates for Maven pom.xml
This document contains a few templates for your pom.xml that you might need when writing a module.
## Contents
1. [Deploy to CraftyServers' Repository](#Deploy-to-CraftyServers'-Repository)
2. [Include CraftyServers' Repository in your pom.xml](#Include-CraftyServers'-Repository-in-your-pom.xml)
3. [Include a module dependency in your pom.xml](#Include-a-module-dependency-in-your-pom.xml)
## Deploy to CraftyServers' Repository
The reopsitory is located at [CraftyServerMC/maven](https://github.com/CraftyServerMC/maven).  
Thanks to user ["emmby"](https://stackoverflow.com/users/82156/emmby) in https://stackoverflow.com/questions/14013644/hosting-a-maven-repository-on-github for a great tutorial!
```XML
<!-- Thanks to user "emmby" in https://stackoverflow.com/questions/14013644/hosting-a-maven-repository-on-github! -->
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>org.craftyserver</groupId> <!-- Always this ID for "CraftyServerMC" -->
  <artifactId>YOUR-ARTIFACT-ID</artifactId> <!-- Name of the module -->
  <version>YOUR-ARTIFACT-VERSION</version> <!-- Version of the module -->
  <distributionManagement>
    <repository>
      <id>internal.repo</id>
      <name>Temporary Staging Repository</name>
      <url>file://${project.build.directory}/mvn-repo</url>
    </repository>
  </distributionManagement>
  <properties>
    <!-- github server corresponds to entry in ~/.m2/settings.xml -->
    <github.global.server>github</github.global.server>
  </properties>
  <build>
    <sourceDirectory>src</sourceDirectory>
    <plugins>
      <plugin>
        <artifactId>maven-deploy-plugin</artifactId>
        <version>2.8.1</version>
        <configuration>
          <altDeploymentRepository>internal.repo::default::file://${project.build.directory}/mvn-repo</altDeploymentRepository>
        </configuration>
      </plugin>
      <plugin>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.8.1</version>
        <configuration>
          <source>1.8</source>
          <target>1.8</target>
        </configuration>
      </plugin>
      <plugin>
        <groupId>com.github.github</groupId>
        <artifactId>site-maven-plugin</artifactId>
        <version>0.12</version>
        <configuration>
          <message>Maven artifacts for ${project.version}</message> <!-- git commit message -->
          <noJekyll>true</noJekyll> <!-- disable webpage processing -->
          <outputDirectory>${project.build.directory}/mvn-repo</outputDirectory> <!-- matches distribution management repository url above -->
          <branch>refs/heads/mvn-repo</branch> <!-- remote branch name -->
          <includes>
            <include>**/*</include>
          </includes>
          <repositoryName>maven</repositoryName> <!-- github repo name -->
          <repositoryOwner>CraftyServerMC</repositoryOwner> <!-- github username  -->
          <merge>true</merge> <!-- Always use merge or you'll wipe the entire Repository! -->
        </configuration>
        <executions>
          <execution>
            <goals>
              <goal>site</goal>
            </goals>
            <phase>deploy</phase>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
</project>
```
### Troubleshooting
 - Make sure you have permission to write to [CraftyServerMC/maven](https://github.com/CraftyServerMC/maven)
 - Make sure to fill out the "Name" field in your Github profile, otherwise commiting won't work!
## Include CraftyServers' Repository in your pom.xml
```XML
<repositories>
  <repository>
    <id>CraftyServer-mvn-repo</id>
    <url>https://github.com/CraftyServerMC/maven/raw/mvn-repo/</url>
    <snapshots>
      <enabled>true</enabled>
      <updatePolicy>always</updatePolicy>
    </snapshots>
  </repository>
</repositories>
```
## Include a module dependency in your pom.xml
```XML
<dependencies>
  <dependency>
    <groupId>org.craftyserver</groupId>
    <artifactId>YOUR-ARTIFACT-ID</artifactId> <!-- Name of the module -->
    <version>YOUR-ARTIFACT-VERSION</version> <!-- Version of the module -->
    <scope>provided</scope>
  </dependency>
</dependencies>
```
