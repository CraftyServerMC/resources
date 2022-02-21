# Templates for Maven pom.xml
This document contains a few templates for a modules' `README.md` file. https://github.com/varunsridharan/action-dynamic-readme is used.
## Contents
1. [Load a dynamic readme template](#load-dynamic)
2. [Version and module stage badges](#version-stage-badges)
3. [Module name and description](#module-name-description)
4. ["This module" section](#this-module)
5. [Maven artifact](#maven-artifact)
6. [Standard readme](#standard-readme)
## Load a dynamic readme template<a id='load-dynamic'></a>
```markdown
<!-- START TEMPLATE.md -->
<!-- END TEMPLATE.md -->
```
Example:
```markdown
<!-- START readme-maven-instructions-repo.md -->
<!-- END readme-maven-instructions-repo.md -->
```
## Version and module stage badges<a id='version-stage-badges'></a>
```markdown
![projectstage](https://img.shields.io/badge/project%20stage-YOURSTAGE-YOURSTAGECOLOR)
![projectstage](https://img.shields.io/badge/version-YOURVERSION-YOURSTAGECOLOR)
```
Example:  
![modulestage](https://img.shields.io/badge/module%20stage-developement-red)
![moduleversion](https://img.shields.io/badge/version-0.0.1-red)
## Module name and description<a id='module-name-description'></a>
```markdown
### (Description of the module)
```
Example:
```markdown
### Self-written modular multi-version Server for *Minecraft&trade;: Java Edition*
```
## "This module" section<a id='this-module'></a>
```markdown
## This module: (Module Name)
(Description)

#### This module does the following:
(List of what it does, using "-")

#### Why is it its own module?
(Reason why this module exists on its own and is not integrated whith another module)
```
Example:
```markdown
## This module: CraftyServer Main
This repository contains the code for the main module, which is the only actually runnable .jar file in the project. If you want to start the server, launch this file.  

#### This module does the following:
 - Provide launchable main class and main method *(Done, but can't be finalized until everything else is done)*
 - Accept connections, recieve, parse and send packages to and from Minecraft Clients *(Done)*
 - Store and access parameters for different client connections *(Not started)*
 - Load, unload, enable and disable modules *(Not started)*
 - Provide Eventmanager & all classes needed for event management *(Works, but misses some features)*
 - Provide data type parser for Minecraft protocol *(VarInt and VarLong are done, others not started)*
 - Provide API to load & save config files *(Works, but misses some features; Might undergo some massive changes)*
 - Provide Logger *(Done)*

#### Why is it its own module?
This is the main module of the server, containing the main method. No other module runs without it.  
```
## Maven artifact<a id='maven-artifact'></a>
See also https://github.com/CraftyServerMC/resources/blob/main/templates/maven.md

````markdown
2. Include artifact:

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
````

Example:
2. Include artifact:

```XML
<dependencies>
  <dependency>
    <groupId>org.craftyserver</groupId>
    <artifactId>craftyserver</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <scope>provided</scope>
  </dependency>
</dependencies>
```

## Standard readme<a id='standard-readme'></a>
````markdown
<!-- START readme-head.md -->
<!-- END readme-head.md -->
![projectstage](https://img.shields.io/badge/project%20stage-YOURSTAGE-YOURSTAGECOLOR)
![projectstage](https://img.shields.io/badge/version-YOURVERSION-YOURSTAGECOLOR)
<!-- START readme-shields.md -->
<!-- END readme-shields.md -->
### (Description of the module)
<!-- START readme-link-to-main-repo.md -->
<!-- END readme-link-to-main-repo.md -->
<!-- START readme-how-to-install.md -->
<!-- END readme-how-to-install.md -->
## This module: (Module Name)
(Description)

#### This module does the following:
(List of what it does, using "-")

#### Why is it its own module?
(Reason why this module exists on its own and is not integrated whith another module)

<!-- START readme-maven-instructions-repo.md -->
<!-- END readme-maven-instructions-repo.md -->

2. Include artifact:

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
````
